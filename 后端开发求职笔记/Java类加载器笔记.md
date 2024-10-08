---
title: 类加载器
url: 类加载器
date: 2024-03-29 15:59:38
tags: [Java]
excerpt: 
index_img: /img/
mermaid: false
---
# 回顾类加载过程

- 类加载过程：加载->连接/链接->初始化
- 连接过程又可以分为三步：验证->准备->解析

加载是类加载过程的第一步，主要完成下面 3 件事情：

1. 通过全类名获取定义此类的二进制字节流
2. 将字节流所代表的静态存储结构转换为方法区的运行时数据结构
3. 在内存中生成一个代表该类的 Class 对象，作为方法区这些数据的访问入口

# 类加载器

## 类加载器的介绍

类加载器赋予了Java类可以被动态加载到JVM中并执行的能力

从上面的介绍可以看出:
1. 类加载器是一个负责加载类的对象，用于实现类加载过程中的加载这一步。
1. 每个 Java 类都有一个引用指向加载它的 ClassLoader。
1. 数组类不是通过 ClassLoader 创建的（数组类没有对应的二进制字节流），是由 JVM 直接生成的。

简单来说，类加载器的主要作用就是加载Java类的字节码(.class)文件到JVM中（在内存中生成一个代表该类的Clasa对象）。

顺带一提，类加载器还可以加载Java应用需要的文本、图像、配置文件、视频等等文件资源

## 类加载器的加载规则

对于大部分类，JVM会根据需要动态加载，这样可以节省内存

已经加载的类会被存放到`ClassLoader`中。
类加载时，系统会首先判断当前类是否被加载过。已经被加载过的类会被直接返回，否则才会尝试加载。

## 类加载器总结

JVM 中内置了三个重要的 ClassLoader：
1. BootstrapClassLoader(启动类加载器)：最顶层的加载类，由 C++实现，通常表示为 null，并且没有父级，主要用来加载 JDK 内部的核心类库（ %JAVA_HOME%/lib目录下的 rt.jar、resources.jar、charsets.jar等 jar 包和类）以及被 -Xbootclasspath参数指定的路径下的所有类。
2. ExtensionClassLoader(扩展类加载器)：主要负责加载 %JRE_HOME%/lib/ext 目录下的 jar 包和类以及被 java.ext.dirs 系统变量所指定的路径下的所有类。
3. AppClassLoader(应用程序类加载器)：面向我们用户的加载器，负责加载当前应用 classpath 下的所有 jar 包和类。

🌈拓展一下：
- rt.jar：rt 代表“RunTime”，rt.jar是 Java 基础类库，包含 Java doc 里面看到的所有的类的类文件。也就是说，我们常用内置库 java.xxx.*都在里面，比如java.util.*、java.io.*、java.nio.*、java.lang.*、java.sql.*、java.math.*。
- Java 9 引入了模块系统，并且略微更改了上述的类加载器。扩展类加载器被改名为平台类加载器（platform class loader）。Java SE 中除了少数几个关键模块，比如说 java.base 是由启动类加载器加载之外，其他的模块均由平台类加载器所加载。

[类加载器层次关系图](https://oss.javaguide.cn/github/javaguide/java/jvm/class-loader-parents-delegation-model.png)

除了 BootstrapClassLoader 是 JVM 自身的一部分之外，其他所有的类加载器都是在 JVM 外部实现的，并且全都继承自 ClassLoader抽象类。这样做的好处是用户可以自定义类加载器，以便让应用程序自己决定如何去获取所需的类。

每个 `ClassLoader` 可以通过`getParent()`获取其父 `ClassLoader`，如果获取到 `ClassLoader` 为`null`的话，那么该类是通过 `BootstrapClassLoader` 加载的。因为`BootstrapClassLoader` 由 C++ 实现，由于这个 C++ 实现的类加载器在 Java 中是没有与之对应的类的，所以拿到的结果是 null。

## 自定义类加载器
除了 BootstrapClassLoader 其他类加载器均由 Java 实现且全部继承自java.lang.ClassLoader。如果我们要自定义自己的类加载器，很明显需要继承 ClassLoader抽象类。

ClassLoader 类有两个关键的方法：
1. protected Class loadClass(String name, boolean resolve)：加载指定二进制名称的类，实现了双亲委派机制 。name 为类的二进制名称，resolve 如果为 true，在加载时调用 resolveClass(Class<?> c) 方法解析该类。
2. protected Class findClass(String name)：根据类的二进制名称来查找类，默认实现是空方法。

如果我们不想打破双亲委派模型，就重写 ClassLoader 类中的 findClass() 方法即可，无法被父类加载器加载的类最终会通过这个方法被加载。但是，如果想打破双亲委派模型则需要重写 loadClass() 方法。

# 双亲委派模型

## 双亲委派模型介绍

类加载器有很多种，当我们想要加载一个类的时候，具体是哪个类加载器加载呢？这就需要提到双亲委派模型了

- ClassLoader 类使用委托模型来搜索类和资源。
- 双亲委派模型要求除了顶层的启动类加载器外，其余的类加载器都应有自己的父类加载器。
- ClassLoader 实例会在试图亲自查找类或资源之前，将搜索类或资源的任务委托给其父类加载器。

各种类加载器之间的 层次关系 被称为类加载器的“双亲委派模型(Parents Delegation Model)”。

[类加载器层次关系图](https://oss.javaguide.cn/github/javaguide/java/jvm/class-loader-parents-delegation-model.png)

注意 ⚠️：双亲委派模型并不是一种强制性的约束，只是 JDK 官方推荐的一种方式。如果我们因为某些特殊需求想要打破双亲委派模型，也是可以的。

双亲不是真的得有“双个”，就像二叉树的父节点一样，有一个上层就行，这个是翻译问题

另外，类加载器之间的父子关系一般不是以继承的关系来实现的，而是通常使用组合(composition)关系来复用父加载器的代码。
```java
public abstract class ClassLoader {
  ...
  // 组合
  private final ClassLoader parent;
  protected ClassLoader(ClassLoader parent) {
       this(checkCreateClassLoader(), parent);
  }
  ...
}
```

⭐️补充：组合是java中一种对象关系的表示方式，它允许一个类持有其它类的实例作为其成员变量
这种关系表达了一种"拥有"或"包含"的关系，其中一个类是另一个类的一部分。

简单来说就是一个类中初始化了另一个类的实例，然后就可以通过这个实例来调用该类的方法，好处就是一个类可以动态组合不同的类，而不必像继承那样静态的在编译时就确定。

当一个类通过组合关系持有其他类的实例时，它可以使用这些实例的成员变量和方法，从而通过委托的方式复用其他类的功能。这使得类之间的关系更加灵活，可以在运行时动态配置成员对象，而不是通过继承关系在编译时静态确定。

面向对象有一条经典的设计原则：组合优于继承，多用组合少用继承。

## 双亲委派模型的执行流程

当一个类接受到加载请求的时候，首先请求转发给父类加载器。父类加载器没有找到所请求的类的情况下，该类加载器再去尝试加载。

流程：
1. 在类加载的时候，系统会首先判断当前类是否被加载过。已经被加载的类会直接返回，否则才会尝试加载（每个父类加载器都会走一遍这个流程）。
1. 类加载器在进行类加载的时候，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成（调用父加载器 loadClass()方法来加载类）。这样的话，所有的请求最终都会传送到顶层的启动类加载器 BootstrapClassLoader 中。
1. 只有当父加载器反馈自己无法完成这个加载请求（它的搜索范围中没有找到所需的类）时，子加载器才会尝试自己去加载（调用自己的 findClass() 方法来加载类）。
1. 如果子类加载器也无法加载这个类，那么它会抛出一个 ClassNotFoundException 异常。

🌈 拓展

JVM 判定两个 Java 类是否相同的具体规则,JVM 不仅要看类的全名是否相同，还要看加载此类的类加载器是否一样。只有两者都相同的情况，才认为两个类是相同的。即使两个类来源于同一个 Class 文件，被同一个虚拟机加载，只要加载它们的类加载器不同，那这两个类就必定不相同。

## 双亲委派模型的好处

避免类的重复加载（JVM 区分不同类的方式不仅仅根据类名，相同的类文件被不同的类加载器加载产生的是两个不同的类），也保证了 Java 的核心 API 不被篡改。
举例：如果自己自定义了一个名为`java.lang.Object`的类，不用双亲委派模型，而是让每个类加载器自己加载自己，那么就会出现两个不同的`Object`类。而双亲委派模型可以保证加载的是JRE里的那个`Object`类。因为`AppClassLoader`会把类的加载委托给`ExtensionClassLoader`，而`ExtClassLoader`又会委托给`BootstrapClassLoader`,`BootstrapClassLoader`会发现自己加载过`Object`类，会直接返回，而不会加载用户自定义的`Object`类。

## 打破双亲委派模型的方法

自定义加载器的话，需要继承 ClassLoader 。如果我们不想打破双亲委派模型，就重写 ClassLoader 类中的 findClass() 方法即可，无法被父类加载器加载的类最终会通过这个方法被加载。

但是，如果想打破双亲委派模型则需要重写 loadClass() 方法。原因如下：
```plaintext
  类加载器在进行类加载的时候，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成（调用父加载器 loadClass()方法来加载类）。
```

重写 loadClass()方法之后，我们就可以改变传统双亲委派模型的执行流程。例如，子类加载器可以在委派给父类加载器之前，先自己尝试加载这个类，或者在父类加载器返回之后，再尝试从其他地方加载这个类。

我们比较熟悉的 Tomcat 服务器为了能够优先加载 Web 应用目录下的类，然后再加载其他目录下的类，就自定义了类加载器 WebAppClassLoader 来打破双亲委托机制。这也是 Tomcat 下 Web 应用之间的类实现隔离的具体原理。
Tomcat 的类加载器的层次结构如下：

[Tomcat 的类加载器的层次结构](https://oss.javaguide.cn/github/javaguide/java/jvm/tomcat-class-loader-parents-delegation-model.png)

Tomcat 这四个自定义的类加载器对应的目录如下：

- CommonClassLoader对应<Tomcat>/common/*
- CatalinaClassLoader对应<Tomcat >/server/*
- SharedClassLoader对应 <Tomcat >/shared/*
- WebAppClassloader对应 <Tomcat >/webapps/<app>/WEB-INF/*

从图中的委派关系中可以看出：

- CommonClassLoader作为 CatalinaClassLoader 和 SharedClassLoader 的父加载器。CommonClassLoader 能加载的类都可以被 CatalinaClassLoader 和 SharedClassLoader 使用。因此，CommonClassLoader 是为了实现公共类库（可以被所有 Web 应用和 Tomcat 内部组件使用的类库）的共享和隔离。
- CatalinaClassLoader 和 SharedClassLoader 能加载的类则与对方相互隔离。CatalinaClassLoader 用于加载 Tomcat 自身的类，为了隔离 Tomcat 本身的类和 Web 应用的类。SharedClassLoader 作为 WebAppClassLoader 的父加载器，专门来加载 Web 应用之间共享的类比如 Spring、Mybatis。
- 每个 Web 应用都会创建一个单独的 WebAppClassLoader，并在启动 Web 应用的线程里设置线程线程上下文类加载器为 WebAppClassLoader。各个 WebAppClassLoader 实例之间相互隔离，进而实现 Web 应用之间的类隔。

单纯依靠自定义类加载器没办法满足某些场景的要求，例如，有些情况下，高层的类加载器需要加载低层的加载器才能加载的类。

比如，SPI 中，SPI 的接口（如 java.sql.Driver）是由 Java 核心库提供的，由BootstrapClassLoader 加载。而 SPI 的实现（如com.mysql.cj.jdbc.Driver）是由第三方供应商提供的，它们是由应用程序类加载器或者自定义类加载器来加载的。默认情况下，一个类及其依赖类由同一个类加载器加载。所以，加载 SPI 的接口的类加载器（BootstrapClassLoader）也会用来加载 SPI 的实现。按照双亲委派模型，BootstrapClassLoader 是无法找到 SPI 的实现类的，因为它无法委托给子类加载器去尝试加载。

再比如，假设我们的项目中有 Spring 的 jar 包，由于其是 Web 应用之间共享的，因此会由 SharedClassLoader 加载（Web 服务器是 Tomcat）。我们项目中有一些用到了 Spring 的业务类，比如实现了 Spring 提供的接口、用到了 Spring 提供的注解。所以，加载 Spring 的类加载器（也就是 SharedClassLoader）也会用来加载这些业务类。但是业务类在 Web 应用目录下，不在 SharedClassLoader 的加载路径下，所以 SharedClassLoader 无法找到业务类，也就无法加载它们。

如何解决这个问题呢？ 这个时候就需要用到 线程上下文类加载器（ThreadContextClassLoader） 了。

拿 Spring 这个例子来说，当 Spring 需要加载业务类的时候，它不是用自己的类加载器，而是用当前线程的上下文类加载器。还记得我上面说的吗？每个 Web 应用都会创建一个单独的 WebAppClassLoader，并在启动 Web 应用的线程里设置线程线程上下文类加载器为 WebAppClassLoader。这样就可以让高层的类加载器（SharedClassLoader）借助子类加载器（ WebAppClassLoader）来加载业务类，破坏了 Java 的类加载委托机制，让应用逆向使用类加载器。

线程线程上下文类加载器的原理是将一个类加载器保存在线程私有数据里，跟线程绑定，然后在需要的时候取出来使用。这个类加载器通常是由应用程序或者容器（如 Tomcat）设置的。

Java.lang.Thread 中的getContextClassLoader()和 setContextClassLoader(ClassLoader cl)分别用来获取和设置线程的上下文类加载器。如果没有通过setContextClassLoader(ClassLoader cl)进行设置的话，线程将继承其父线程的上下文类加载器。





