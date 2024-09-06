---
title: Spring6启示录
date: 2024-05-06 16:41:30
tags:
---

## Spring启示录

### OCP开闭原则

在软件开发过程中应当对扩展开放，对修改关闭

### 依赖倒置

- Dependence Inversion Principle(DIP)
- 要倡导面向抽象编程，面向接口编程，不要面向具体编程，让上层不再依赖下层，下面改动了，上面的代码不会受到牵连。这样可以大大降低程序的耦合度，耦合度低了，扩展力就强了，同时代码复用性也会增强。（软件七大开发原则都是在为解耦合服务）

- Spring框架可以帮助我们创建对象，并且可以帮助我们维护对象和对象之间的关系

- Spring其实就是一个管理Bean对象的工厂

### 控制反转

- Inversion of Control(IoC)

控制反转的核心是：将对象的创建权交出去，将对象和对象之间关系的管理权交出去，由第三方容器来负责创建与维护。

- 控制反转常见的实现方式：依赖注入（Dependency Injection，简称DI。

## Spring概述

spring = IOC + AOP(面向切面编程)

### Spring8大模块

### Spring 特点

1. 轻量
  a. 小
  b. 非侵入式：Spring应用中的对象不依赖于Spring的特定类，也就是说 我们自己创建的对象不依赖spring容器
2. IoC
3. 面向切面(AOP)
4. 容器
    Spring包含并管理应用对象的配置和生命周期，在这个意义上它是一种容器，你可以配置你的每个bean如何被创建——基于一个可配置原型（prototype），你的bean可以创建一个单独的实例或者每次需要时都生成一个新的实例——以及它们是如何相互关联的。
5. 框架
    Spring可以将简单的组件配置、组合成为复杂的应用。在Spring中，应用对象被声明式地组合，典型地是在一个XML文件里。Spring也提供了很多基础功能（事务管理、持久化框架集成等等），将应用逻辑的开发留给了你。

## Spring 入门程序

### 第一个Spring程序

- Spring的配置文件：beans.xml 放在类的根路径下。
配置文件中进行bean的配置
  - id属性：代表对象的唯一标识。
  - class属性:用来指定要创建的java类的类名，这个类名必须是全限定类名（包含包名

- Spring是通过反射机制调用类的无参构造方法来创建对象的。

### Spring6 启用Log4j2日志框架

第一步：引入Log4j2的依赖

```xml
<!--log4j2的依赖-->
<dependency>
  <groupId>org.apache.logging.log4j</groupId>
  <artifactId>log4j-core</artifactId>
  <version>2.19.0</version>
</dependency>
<dependency>
  <groupId>org.apache.logging.log4j</groupId>
  <artifactId>log4j-slf4j2-impl</artifactId>
  <version>2.19.0</version>
</dependency>

```

第二步：在类的根路径下提供log4j2.xml配置文件（文件名固定为：log4j2.xml，文件必须放到类根路径下。）

```xml
<?xml version="1.0" encoding="UTF-8"?>

<configuration>

    <loggers>
        <!--
            level指定日志级别，从低到高的优先级：
                ALL < TRACE < DEBUG < INFO < WARN < ERROR < FATAL < OFF
        -->
        <root level="DEBUG">
            <appender-ref ref="spring6log"/>
        </root>
    </loggers>

    <appenders>
        <!--输出日志信息到控制台-->
        <console name="spring6log" target="SYSTEM_OUT">
            <!--控制日志输出的格式-->
            <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss SSS} [%t] %-3level %logger{1024} - %msg%n"/>
        </console>
    </appenders>

</configuration>

```

第三步：使用日志框架

## 四、Spring对IoC的实现

### IoC控制反转

- 控制反转是一种思想。

- 控制反转是为了降低程序耦合度，提高程序扩展力，达到OCP原则，达到DIP原则。

- 控制反转，反转的是什么？

  - 将对象的创建权利交出去，交给第三方容器负责。

  - 将对象和对象之间关系的维护权交出去，交给第三方容器负责。

- 控制反转这种思想如何实现呢？

  - DI（Dependency Injection）：依赖注入

### IoC依赖注入

依赖注入实现了控制反转的思想。

Spring通过依赖注入的方式来完成Bean管理的。

Bean管理说的是：Bean对象的创建，以及Bean对象中属性的赋值（或者叫做Bean对象之间关系的维护）。

依赖注入：

- 依赖指的是对象和对象之间的关联关系。

- 注入指的是一种数据传递行为，通过注入行为来让对象和对象产生关系。

依赖注入常见的实现方式包括两种：

set注入:基于**set方法**实现，底层通过反射机制调用属性对应的set方法然后给属性赋值。因此这种方法要求属性必须对外暴露set方法。

总结：set注入的核心实现原理：通过反射机制调用set方法来给属性赋值，让两个对象之间产生关系。

构造注入:通过调用**构造方法**来给属性赋值。

通过测试得知，通过构造方法注入的时候：

- 可以通过下标
- 可以通过参数名
- 也可以不指定下标和参数名，可以类型自动推断。

### p命名空间注入

p命名空间注入是基于setter方法的，所以需要对应的属性提供setter方法。

### c命名空间注入

c命名空间是简化构造方法注入的,需要提供构造方法

- 注意：不管是p命名空间还是c命名空间，注入的时候都可以注入简单类型以及非简单类型。

### util命名空间

使用util命名空间可以让配置复用。

### 基于XML的自动装配

Spring还可以完成自动化的注入，自动化注入又被称为自动装配。它可以根据名字进行自动装配，也可以根据类型进行自动装配。

如果根据名称装配(byName)，底层会调用set方法进行注入。
例如：setAge() 对应的名字是age，setPassword()对应的名字是password，setEmail()对应的名字是email。

当byType进行自动装配的时候，配置文件中某种类型的Bean必须是唯一的

### Spring 引入外部配置文件

## Bean的作用域

### 单例 singleton

默认情况下，Spring的IoC容器创建的Bean对象是单例的。

Bean对象的创建是在初始化Spring上下文的时候就完成的。

### 多例 prototype

如果想让Spring的Bean对象以多例的形式存在，可以在bean标签中指定scope属性的值为：prototype

scope如果没有配置，它的默认值是什么呢？默认值是singleton，单例的。

### 其他scope

## Gof (gang of four) 之工厂模式

设计模式: 一种可以被重复利用的方案

工厂模式是解决对象创建问题的，所以工厂模式属于创建型设计模式。这里为什么学习工厂模式呢？这是因为Spring框架底层使用了大量的工厂模式。

GoF23种设计模式可分为三大类:

- 创建型（5个）：解决对象创建问题。
- 结构型(7个)：一些类或对象组合在一起的经典结构。
- 行为型（11个）：解决类或对象之间的交互问题。

### 工厂模式的三种形态

1. 简单工厂模式（Simple Factory）：不属于23种设计模式之一。简单工厂模式又叫做：静态 工厂方法模式。简单工厂模式是工厂方法模式的一种特殊实现。
2. 工厂方法模式（Factory Method）：是23种设计模式之一。
3. 抽象工厂模式（Abstract Factory）：是23种设计模式之一。

### 简单工厂模式

单工厂模式的角色包括三个：

1. 抽象产品角色
2. 具体产品角色
3. 工厂类角色

抽象产品角色：

```java
package com.powernode.factory;

/**
 * 武器（抽象产品角色）
 * @author 动力节点
 * @version 1.0
 * @className Weapon
 * @since 1.0
 **/
public abstract class Weapon {
    /**
     * 所有的武器都有攻击行为
     */
    public abstract void attack();
}

```

具体产品角色：

```java
package com.powernode.factory;

/**
 * 坦克（具体产品角色）
 * @author 动力节点
 * @version 1.0
 * @className Tank
 * @since 1.0
 **/
public class Tank extends Weapon{
    @Override
    public void attack() {
        System.out.println("坦克开炮！");
    }
}


```

```java
package com.powernode.factory;

/**
 * 战斗机（具体产品角色）
 * @author 动力节点
 * @version 1.0
 * @className Fighter
 * @since 1.0
 **/
public class Fighter extends Weapon{
    @Override
    public void attack() {
        System.out.println("战斗机投下原子弹！");
    }
}


```

```java
package com.powernode.factory;

/**
 * 匕首（具体产品角色）
 * @author 动力节点
 * @version 1.0
 * @className Dagger
 * @since 1.0
 **/
public class Dagger extends Weapon{
    @Override
    public void attack() {
        System.out.println("砍他丫的！");
    }
}


```

工厂类角色：

```java
package com.powernode.factory;

/**
 * 工厂类角色
 * @author 动力节点
 * @version 1.0
 * @className WeaponFactory
 * @since 1.0
 **/
public class WeaponFactory {
    /**
     * 根据不同的武器类型生产武器
     * @param weaponType 武器类型
     * @return 武器对象
     */
    public static Weapon get(String weaponType){
        if (weaponType == null || weaponType.trim().length() == 0) {
            return null;
        }
        Weapon weapon = null;
        if ("TANK".equals(weaponType)) {
            weapon = new Tank();
        } else if ("FIGHTER".equals(weaponType)) {
            weapon = new Fighter();
        } else if ("DAGGER".equals(weaponType)) {
            weapon = new Dagger();
        } else {
            throw new RuntimeException("不支持该武器！");
        }
        return weapon;
    }
}


```

测试程序（客户端程序）：

```java
package com.powernode.factory;

/**
 * @author 动力节点
 * @version 1.0
 * @className Client
 * @since 1.0
 **/
public class Client {
    public static void main(String[] args) {
        Weapon weapon1 = WeaponFactory.get("TANK");
        weapon1.attack();

        Weapon weapon2 = WeaponFactory.get("FIGHTER");
        weapon2.attack();

        Weapon weapon3 = WeaponFactory.get("DAGGER");
        weapon3.attack();
    }
}

```

## 依赖注入

### set 注入(主要应用)

- [ ] set注入的核心实现原理：通过反射机制调用set方法来给属性赋值，让两个对象之间产生关系。
- [ ] property标签的name是：setUserDao()方法名演变得到的
- [ ] 注入外部bean

> > - [ ] 外部Bean的特点：bean定义到外面，在property标签中使用ref属性进行注入。通常这种方式是常用。 [ ] 注入内部bean

- [ ] 注入简单类型

> > - [ ] 如果给简单类型赋值，使用value属性或value标签。而不是ref。
> > - [ ] 简单类型包括哪些呢？

- 基本数据类型
- 基本数据类型对应的包装类
- String或其他的CharSequence子类
- Number子类
- Date子类
- Enum子类
- URI
- URL
- Temporal子类
- Locale
- Class
- 另外还包括以上简单值类型对应的数组类型
  > > - [ ] 需要注意的是：
- 如果把Date当做简单类型的话，日期字符串格式不能随便写。格式必须符合Date的toString()方法格式。显然这就比较鸡肋了。如果我们提供一个这样的日期字符串：2010-10-11，在这里是无法赋值给Date类型的属性的。
- spring6之后，当注入的是URL，那么这个url字符串是会进行有效性检测的。如果是一个存在的url，那就没问题。如果不存在则报错。

---

- [ ] 级联属性赋值

> > - [ ] 要点：

- 在spring配置文件中，如上，注意顺序。
- 在spring配置文件中，clazz属性必须提供getter方法。

- [ ] 注入数组
      要点：

- 如果数组中是简单类型，使用value标签。
- 如果数组中是非简单类型，使用ref标签。

- [ ] 注入list集合(有序可重复)

  - 同上，只要把array标签改为list
  - 注意：注入List集合的时候使用list标签，如果List集合中是简单类型使用value标签，反之使用ref标签。

- [ ] 注入set集合(无序不可重复)

  - 使用`<set>`标签

  - set集合中元素是简单类型的使用value标签，反之使用ref标签。

  - [ ] 注入map集合
        要点：

  - 使用`<map>`标签
  - 如果key是简单类型，使用 key 属性，反之使用 key-ref 属性。
  - 如果value是简单类型，使用 value 属性，反之使用 value-ref 属性。

  - [ ] p命名空间注入

  使用p命名空间注入的前提条件包括两个：

  - 第一：在XML头部信息中添加p命名空间的配置信息：xmlns:p="<http://www.springframework.org/schema/p>"
  - 第二：p命名空间注入是基于setter方法的，所以需要对应的属性提供setter方法。

  - [ ] c命名空间注入

  c命名空间是简化构造方法注入的。

  - 使用c命名空间的两个前提条件：
    第一：需要在xml配置文件头部添加信息：xmlns:c="<http://www.springframework.org/schema/c>"
  - 第二：需要提供构造方法。

  - [ ] util 命名空间

  - 使用util命名空间可以让配置复用。

### 构造注入

- [ ] 通过测试得知，通过构造方法注入的时候

- 可以通过下标
- 可以通过参数名
- 也可以不指定下标和参数名，可以类型自动推断。
- spring在装配方面做的还是比较健壮的

### 基于XML的自动装配

- [ ] 根据名称自动装配

- Spring还可以完成自动化的注入，自动化注入又被称为自动装配。它可以根据名字进行自动装配，也可以根据类型进行自动装配
- 这说明，如果根据名称装配(byName)，底层会调用set方法进行注入。
  例如：setAge() 对应的名字是age，setPassword()对应的名字是password，setEmail()对应的名字是email。

- [ ] 根据类型自动装配

- 配置文件中某种类型的Bean必须是唯一的，不能出现多个。

### spring引入外部属性配置文件

### Bean的作用域

- [ ] Spring的IoC容器中，默认情况下，Bean对象是单例的
- [ ] 默认情况下，Bean对象的创建是在初始化Spring上下文的时候就完成的
- [ ] 如果想让Spring的Bean对象以多例的形式存在，可以在bean标签中指定scope属性的值为：prototype，**这样Spring会在每一次执行getBean()方法的时候创建Bean对象**，调用几次则创建几次。

- scope属性的值不止两个，它一共包括8个选项：
- singleton：默认的，单例。
- prototype：原型。每调用一次getBean()方法则获取一个新的Bean对象。或每次注入的时候都是新对象。
- request：一个请求对应一个Bean。仅限于在WEB应用中使用。
- session：一个会话对应一个Bean。仅限于在WEB应用中使用。
- global session：portlet应用中专用的。如果在Servlet的WEB应用中使用global session的话，和session一个效果。（portlet和servlet都是规范。servlet运行在servlet容器中，例如Tomcat。portlet运行在portlet容器中。）
- application：一个应用对应一个Bean。仅限于在WEB应用中使用。
- websocket：一个websocket生命周期对应一个Bean。仅限于在WEB应用中使用。
- 自定义scope：很少使用。

### Gof FactoryMode 工厂模式

- [ ] 简单工厂模式

> > - [ ] 简单工厂模式的优点：

- 客户端程序不需要关心对象的创建细节，需要哪个对象时，只需要向工厂索要即可，初步实现了责任的分离。客户端只负责“消费”，工厂负责“生产”。生产和消费分离。
  > > - [ ] 简单工厂模式的缺点：
- 缺点1：工厂类集中了所有产品的创造逻辑，形成一个无所不知的全能类，有人把它叫做上帝类。显然工厂类非常关键，不能出问题，一旦出问题，整个系统瘫痪。
- 缺点2：不符合OCP开闭原则，在进行系统扩展时，需要修改工厂类。Spring中的BeanFactory就使用了简单工厂模式。

- [ ] 工厂方法模式

> > - [ ] 工厂方法模式既保留了简单工厂模式的优点，同时又解决了简单工厂模式的缺点。
> >       工厂方法模式的角色包括：

- 抽象工厂角色
- 具体工厂角色
- 抽象产品角色
- 具体产品角色

## Bean的实例化方式

### 1. 构造方法

- [ ] 在配置文件中配置类的全路径，spirng直接调用该类的无参构造方法获取bean对象

### 2. 简单工厂模式

- [ ] 通过简单工厂模式，调用`工厂`的静态方法`get()`获取bean对象
- [ ] 工厂类里的方法是静态方法，所以不需要spring工厂的实例

### 3. 通过factory-bean实例化(本质上是工厂方法模式)

- [ ] 工厂类里的方法是非静态方法，所工厂类也必须被spring管理起来
- [ ] 标签也要多一个 因为得告诉spring是创建哪个`工厂` 的 哪个`对象`
      所以得指定哪个对象(factory-bean)的哪个方法(factory-method)

### 4. 通过FactoryBean接口实例化

- [ ] 只要实现接口和接口的抽象方法 就可以不需要指定factory-bean 和
      factory-method。是对第三种方法的简化
- [ ] 因为实现了接口所以直接认为你这个类的对象就是一个豆子
      td因为实现了接口所以直接认为你这个类的对象就是一个豆子

### BeanFactory 和 FactoryBean 的区别

- [ ] BeanFactory

- Spring IoC容器的顶级对象，BeanFactory被翻译为“Bean工厂”，在Spring的IoC容器中，“Bean工厂”负责创建Bean对象。
  BeanFactory是工厂。

- [ ] FactoryBean

- 它是一个**Bean**，是一个能够辅助Spring实例化其它Bean对象的一个Bean。
  在Spring中，Bean可以分为两类：
  ● 第一类：普通Bean
  ● 第二类：工厂Bean（记住：工厂Bean也是一种Bean，只不过这种Bean比较特殊，它可以辅助Spring实例化其它Bean对象。）

### 注入自定义 Date (工厂Bean的实际应用)

### Bean 的生命周期(可分为5步7步10步)(也就是bean对象从开始创建到消亡的整个过程)

- [ ] 当想在具体某个生命周期做指定操作时可以用到
- 第一步：实例化Bean
- 第二步：Bean属性赋值
- 第三步：初始化Bean 需要手动指定 使用init-method标签
  \*\* bean后处理器的before方法
- 第四步：使用Bean
  \*\* bean后处理器的after方法
- 第五步：销毁Bean 使用手动指定 用destory-method标签

### Bean的作用域不同，管理方式不同

- 对于singleton作用域的Bean，Spring 能够精确地知道该Bean何时被创建，何时初始化完成，以及何时被销毁；
- 而对于 prototype 作用域的 Bean，Spring 只负责创建，当容器创建了
  Bean 的实例后，Bean 的实例就交给客户端代码管理，Spring 容器将不再跟踪其生命周期。

### 自己new的对象可以让Spring管理

```java
public class RegisterBeanTest {

  @Test
    public void testBeanRegister(){
      // 自己new的对象
      User user = new User();
      System.out.println(user);

      // 创建 默认可列表BeanFactory 对象
      DefaultListableBeanFactory factory = new DefaultListableBeanFactory();
      // 注册Bean
      factory.registerSingleton("userBean", user);
      // 从spring容器中获取bean
      User userBean = factory.getBean("userBean", User.class);
      System.out.println(userBean);
    }
}

```

## Bean的循环依赖问题

### `singleton` + set注入

循环依赖没有问题,解决方法如下:

- [ ] spring容器一旦将bean创建出来就立刻进行`曝光`
      (不赋值就告诉大家我可以被使用啦！！)
- [ ] 曝光之后再进行赋值

### `prototype` + set注入

- [ ] 当循环依赖的 **所有** Bean的scope="prototype"的时候，产生的循环依赖，Spring是无法解决的，会出现BeanCurrentlyInCreationException异常。
  > > - [ ] new ClassPathApplicationContext的时候不会new对象
  > >       ，只有在getBean的时候才会创建对象,会无限递归
- [ ] 当循环依赖的一个是单例时，就不会出现问题

### `singleton`/`prototype`+ 构造注入

- [ ] 有异常，因为创建对象和给属性赋值是同时进行的，不给属性赋值对象就创建不出来

### Spring解决循环依赖的机理

- [ ] Spring只能解决setter方法注入的单例bean之间的循环依赖。
ClassA依赖ClassB，ClassB又依赖ClassA，形成依赖闭环。
Spring在创建ClassA对象后，不需要等给属性赋值，直接将其曝光到bean缓存当中。在解析ClassA的属性时，又发现依赖于ClassB，再次去获取ClassB，当解析ClassB的属性时，又发现需要ClassA的属性，但此时的ClassA已经被提前曝光加入了正在创建的bean的缓存中，则无需创建新的的ClassA的实例，直接从缓存中获取即可。从而解决循环依赖问题。

## 回顾反射机制

### 方法调用的四个要素

- 哪个对象
- 哪个方法
- 哪个参数
- 返回什么值

## 全注解式开发

### 负责声明bean的注解

- @Component
- @Controller
- @Service
- @Repository

@Controller、@Service、@Repository这三个注解都是@Component注解的别名。其实这四个注解的功能一样，但是为了增强程序的可读性

- 控制器类上使用：Controller
- service类上使用：Service
- dao类上使用：Repository

他们都是只有一个value属性。value属性用来指定bean的id，也就是bean的名字。

### spring注解的使用

1. 加入AOP依赖(一般会加入spring-context依赖后会关联加入，所以这一步不用做)
2. 配置文件中配置context命名空间
3. 配置包扫描
4. Bean上使用注解

> [!TIP]
> 如果注解的属性名是value，那么可以省略
  如果把value属性彻底去掉，spring会被Bean自动取名，并且默认名字的规律是：Bean类名首字母小写后面不变。

如果是多个包怎么办？有两种解决方案：

- 第一种：在配置文件中指定多个包，用逗号隔开。
- 第二种：指定多个包的共同父包。

### 选择性实例化Bean

假设在某个包下有很多Bean，有的Bean上标注了Component，有的标注了Controller，有的标注了Service，有的标注了Repository，现在由于某种特殊业务的需要，只允许其中所有的Controller参与Bean管理

- 修改配置文件就行，用到再去查

### 负责注入的注解

@Component @Controller @Service @Repository 这四个注解是用来**声明**Bean的，声明后这些Bean将被实例化。接下来我们看一下，如何给Bean的属性赋值。给Bean属性**赋值**需要用到这些注解：

- @Value 负责注入简单类型
  - @Value注解可以直接使用在属性上，也可以使用在setter方法上,以及构造方法的形参上。
  - 为了简化代码，以后我们一般不提供setter方法，直接在属性上使用@Value注解完成属性赋值。

- @Autowired 单独使用@Autowired注解，默认根据类型装配。【默认是byType】
  - @Autowired注解可以用来注入非简单类型。被翻译为：自动连线的，或者自动装配。单独使用@Autowired注解，默认根据类型装配。【默认是byType】
  - 当有参数的构造方法只有一个时，@Autowired注解可以省略。如果有多个构造方法，@Autowired肯定是不能省略的。
  - 可以直接使用在属性上，也可以使用在setter方法上,以及构造方法、构造方法参数上

- 如一个要装配的接口有不止一个实现类，则配合@Qualified使用才能byName进行装配

- @Resource注解默认根据属性名进行装配。
  - @Resource注解也可以完成非简单类型注入。
  - 与@Autowired注解的区别：
    - @Resource注解是JDK扩展包中的，也就是说属于JDK的一部分。所以该注解是标准注解，更加具有通用性。
    - @Autowired注解是Spring框架自己的。
    - @Resource注解默认根据名称装配byName，未指定name时，使用属性名作为name。通过name找不到的话会自动启动通过类型byType装配。
    - @Resource注解用在属性上、setter方法上。
    - @Autowired注解用在属性上、setter方法上、构造方法上、构造方法参数上。

## GOF代理模式

### 对代理模式的理解

代理模式中有一个非常重要的特点：对于客户端程序来说，使用代理对象时就像在使用目标对象一样。【在程序中，目标需要被保护时】

代理模式是GoF23种设计模式之一。属于结构型设计模式。

代理模式的作用是：为其他对象提供一种代理以控制对这个对象的访问。在某些情况下，一个客户不想或者不能直接引用一个对象，此时可以通过一个称之为“代理”的第三者来实现间接引用。代理对象可以在客户端和目标对象之间起到**中介**的作用，并且可以通过代理对象去掉客户不应该看到的内容和服务或者添加客户需要的额外服务。 通过**引入一个新的对象**来实现对真实对象的操作或者将新的对象作为真实对象的一个替身，这种实现机制即为代理模式，**通过引入代理对象来间接访问一个对象**，这就是代理模式的模式动机。
代理模式中的角色：

- 代理类（代理主题）
- 目标类（真实主题）
- 代理类和目标类的公共接口（抽象主题）：客户端在使用代理类时就像在使用目标类，不被客户端所察觉，所以代理类和目标类要有共同的行为，也就是实现共同的接口。

### 动态代理

在内存当中动态生成类的技术常见的包括：

- JDK动态代理技术：只能代理接口。
- CGLIB动态代理技术：CGLIB(Code Generation Library)是一个开源项目。是一个强大的，高性能，高质量的Code生成类库，它可以在运行期扩展Java类与实现Java接口。它既可以代理接口，又可以代理类，底层是通过**继承**的方式实现的,因此被代理的目标类不能用`final`修饰。性能比JDK动态代理要好。（底层有一个小而快的字节码处理框架ASM。）
- Javassist动态代理技术：Javassist是一个开源的分析、编辑和创建Java字节码的类库。是由东京工业大学的数学和计算机科学系的 Shigeru Chiba （千叶 滋）所创建的。它已加入了开放源代码JBoss 应用服务器项目，通过使用Javassist对字节码操作为JBoss实现动态"AOP"框架。

### 静态代理和动态代理的区别

静态代理和动态代理都是在面向对象编程中常见的设计模式，它们都允许一个对象在另一个对象的基础上提供额外的功能。它们的主要区别在于代理类的创建时间和绑定方式。

1. 静态代理：
静态代理是在编译时就已经确定了的代理关系。在静态代理中，代理类在编译期间就已经创建好，并且代理类和被代理类的关系在编译时确定，不能动态改变。

特点：
代理类和被代理类在编译期间确定。
需要为每一个被代理类编写一个对应的代理类。
编译时就已确定代理关系，不灵活。

2. 动态代理：
动态代理是在运行时创建的代理对象，代理类在程序运行时动态生成，而不是在编译期间确定。Java 中的动态代理主要是通过 java.lang.reflect.Proxy 类来实现。

特点：
代理类是在运行时动态生成的。
不需要为每一个被代理类编写一个对应的代理类，可以通过反射机制动态处理。
在运行时可以动态改变代理关系，更加灵活。

应用场景：

- 静态代理： 适用于被代理类较少且不需要频繁变更代理关系的情况，比如安全检查、日志记录等。
- 动态代理： 适用于被代理类较多或者代理关系需要经常变更的情况，比如 AOP（面向切面编程）、RPC（远程过程调用）等。

总的来说，动态代理相对于静态代理更加灵活，因为它允许在运行时动态生成代理对象，而无需在编译时确定。这使得动态代理在一些需要动态管理和调整代理关系的场景下更为实用。

## 面向切面编程的AOP(Aspect Oriented Programming)

- AOP底层使用的是动态代理实现
- Spring的AOP使用的动态代理是：JDK动态代理 + CGLIB动态代理技术。Spring在这两种动态代理中灵活切换，如果是代理接口，会默认使用JDK动态代理，如果要代理某个类，这个类没有实现接口，就会切换使用CGLIB

### AOP介绍

一般一个系统当中都会有一些系统服务，例如：日志、事务管理、安全等。这些系统服务被称为：交叉业务

如果在每一个业务处理过程当中，都掺杂这些交叉业务代码进去的话，存在两方面问题：

- 第一：交叉业务代码在多个业务流程中反复出现，显然这个交叉业务代码没有得到复用。并且修改这些交叉业务代码的话，需要修改多处。
- 第二：程序员无法专注核心业务代码的编写，在编写核心业务代码的同时还需要处理这些交叉业务。

- 用一句话总结AOP：将与核心业务无关的代码独立的抽取出来，形成一个独立的组件，然后以横向交叉的方式应用到业务流程当中的过程被称为AOP。

AOP的优点:

- 第一：代码复用性增强。
- 第二：代码易维护。
- 第三：使开发者更关注业务逻辑。

### AOP七大术语

- [ ] 切面：程序中和业务逻辑没有关系的通用代码(交叉业务)

  - [ ] 连接点 Joinpoint

    > > - [ ] 在程序的整个执行流程中，可以织入切面的位置。方法的执行前后，异常抛出之后等位置。

  - [ ] 切点 Pointcut

    > > - [ ] 在程序执行流程中，真正织入切面的方法。（一个切点对应多个连接点）

  - [ ] 通知 Advice
    > > - [ ] 通知又叫增强，就是具体你要织入的代码。
  - [ ] 切面Aspect

    > > - [ ] 切点 + 通知就是切面。

  - [ ] 织入 Weaving
    > > - [ ] 把通知应用到目标对象上的过程。
  - [ ] 代理对象 Proxy
    > > - [ ] 一个目标对象被织入通知后产生的新对象。
  - [ ] 目标对象 Target
    > > - [ ] 被织入通知的对象。

 切点表达式

```java
execution([访问控制权限修饰符] 返回值类型 [全限定类名]方法名(形式参数列表) [异常])
```

### 使用Spring的AOP

#### 切面的先后顺序

- [ ] 可以使用@Order注解来标识切面类，为@Order注解的value指定一个整数型的数字，数字越小，优先级越高。

```java
@Order(1) //设置优先级
```

#### 通用切点

- 将切点表达式单独的定义出来，在需要的位置引入即可

#### 连接点(Joinpoint)

- [ ] getSignature 获取目标方法的签名

```java
public 开始一直到{}之前
```

#### 全注解开发AOP

- [ ] 编写一个类来代替spring配置文件

```java
package com.powernode.spring6.service;

import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.EnableAspectJAutoProxy;

@Configuration
@ComponentScan("com.powernode.spring6.service")
@EnableAspectJAutoProxy(proxyTargetClass = true)
public class Spring6Configuration {
}
```

- [ ] 因为xml文件没了 所以生成对象的时候也要有所变化

```java
@Test
public void testAOPWithAllAnnotation(){
    ApplicationContext applicationContext = new AnnotationConfigApplicationContext(Spring6Configuration.class);
    OrderService orderService = applicationContext.getBean("orderService", OrderService.class);
    orderService.generate();
}
```

## spring 对事务的支持

### 事务概述

- 什么是事务
  - 在一个业务流程当中，通常需要多条DML（insert delete update）语句共同联合才能完成，这多条DML语句必须同时成功，或者同时失败，这样才能保证数据的安全。
  - 多条DML要么同时成功，要么同时失败，这叫做事务。
  - 事务：Transaction（tx）
- 事务的四个处理过程：
  - 第一步：开启事务 (start transaction)
  - 第二步：执行核心业务代码
  - 第三步：提交事务（如果核心业务处理过程中没有出现异常）(commit transaction)
  - 第四步：回滚事务（如果核心业务处理过程中出现异常）(rollback transaction)
- 事务的四个特性：
  - A 原子性：事务是最小的工作单元，不可再分。
  - C 一致性：事务要求要么同时成功，要么同时失败。事务前和事务后的总量不变。
  - I 隔离性：事务和事务之间因为有隔离性，才可以保证互不干扰。
  - D 持久性：持久性是事务结束的标志。

### 事务的传播行为

- [ ] 在service类中有a()方法和b()方法，a()方法上有事务，b()方法上也有事务，当a()方法执行过程中调用了b()方法，事务是如何传递的？合并到一个事务里？还是开启一个新的事务？这就是事务传播行为。

```java
@Transactional(propagation = Propagation.REQUIRED)
```

一共有七种传播行为：

- REQUIRED：支持当前事务，如果不存在就新建一个(默认)【没有就新建，有就加入】
- SUPPORTS：支持当前事务，如果当前没有事务，就以非事务方式执行【有就加入，没有就不管了】
- MANDATORY：必须运行在一个事务中，如果当前没有事务正在发生，将抛出一个异常【有就加入，没有就抛异常】
- REQUIRES_NEW：开启一个新的事务，如果一个事务已经存在，则将这个存在的事务挂起【不管有没有，直接开启一个新事务，开启的新事务和之前的事务不存在嵌套关系，之前事务被挂起】
- NOT_SUPPORTED：以非事务方式运行，如果有事务存在，挂起当前事务【不支持事务，存在就挂起】
- NEVER：以非事务方式运行，如果有事务存在，抛出异常【不支持事务，存在就抛异常】
- NESTED：如果当前正有一个事务在进行中，则该方法应当运行在一个嵌套式事务中。被嵌套的事务可以独立于外层事务进行提交或回滚。如果外层事务不存在，行为就像REQUIRED一样。【有事务的话，就在这个事务里再嵌套一个完全独立的事务，嵌套的事务可以独立的提交和回滚。没有事务就和REQUIRED一样。】

### 事物的隔离级别

- 脏读：读取到没有提交到数据库的数据(缓存中的数据)，叫做脏读。
- 不可重复读：在同一个事务当中，第一次和第二次读取的数据不一样。
- 幻读：读到的数据是假的。多事务并发一定会产生幻读问题。

```java
@Transactional(isolation = Isolation.READ_COMMITTED)
```

> > - [ ] 其中可以设置的隔离级别有以下四种

- Default
- read_uncommitted
- READ_COMMITTED
- repeatable_read
- serializable

### 事物超时

```java
@Transactional(timeout = 10)
```

- 以上代码表示设置事务的超时时间为10秒。
- 表示超过10秒如果该事务中所有的DML语句还没有执行完毕的话，最终结果会选择回滚。
- 默认值-1，表示没有时间限制。
- 这里有个坑，事务的超时时间指的是哪段时间？:在当前事务当中，最后一条DML语句执行`之前`的时间。如果最后一条DML语句后面很有很多业务逻辑，这些业务代码执行的时间不被计入超时时间。

### 只读事务

```java
@Transactional(readOnly = true)
```

- 将当前事务设置为只读事务，在该事务执行过程中只允许select语句执行，delete insert update均不可执行。
  该特性的作用是：启动spring的优化策略。提高select语句执行效率。
  如果该事务中确实没有增删改操作，建议设置为只读事务。

### 设置哪些异常回滚事务

```java
@Transactional(rollbackFor = RuntimeException.class)
```

- 表示只有发生RuntimeException异常或该异常的子类异常才回滚。

### 设置哪些异常不回滚事务

```java
@Transactional(noRollbackFor = NullPointerException.class)
```

表示发生NullPointerException或该异常的子类异常不回滚，其他异常则回滚。

### 事务的全注解开发

编写一个类来代替配置文件

## Spring6整合JUnit5

### Spring对JUnit4的支持

:wq
Spring提供的方便主要是这几个注解：

- @RunWith(SpringJUnit4ClassRunner.class)
- @ContextConfiguration("classpath:spring.xml")

- 在单元测试类上使用这两个注解之后，在单元测试类中的属性上可以使用@Autowired。比较方便。

### Spring对JUnit5的支持

在JUnit5当中，可以使用Spring提供的以下两个注解，标注到单元测试类上，这样在类当中就可以使用@Autowired注解了。

- @ExtendWith(SpringExtension.class)
- @ContextConfiguration("classpath:spring.xml")

## Spring6集成MyBatis3.5

```java
public interface AccountMapper {
    // 接口定义的方法
}

@Repository
public class AccountMapperImpl implements AccountMapper {
    // 实现接口定义的方法
}

@Service
public class AccountService {

    @Autowired
    private AccountMapper accountMapper;

    // 类的其余部分
}

```

- [ ] 在这个例子中，AccountMapper 是一个接口，AccountMapperImpl 是实现了这个接口的类。在 AccountService 类中，通过 @Autowired 注解将 accountMapper 字段注入为 AccountMapper 接口的实现类的一个实例。

## spring中的八大模式

### 简单工厂模式

BeanFactory的getBean()方法，通过唯一标识来获取Bean对象。是典型的简单工厂模式（静态工厂模式）；

### 工厂方法模式

FactoryBean是典型的工厂方法模式。在配置文件中通过factory-method属性来指定工厂方法，该方法是一个实例方法。

### 单例模式

Spring用的是双重判断加锁的单例模式。

### 代理模式

Spring的AOP就是使用了动态代理实现的。

### 装饰器模式

JavaSE中的IO流是非常典型的装饰器模式。

Spring 中配置 DataSource 的时候，这些dataSource可能是各种不同类型的，比如不同的数据库：Oracle、SQL Server、MySQL等，也可能是不同的数据源：比如apache 提供的org.apache.commons.dbcp.BasicDataSource、spring提供的org.springframework.jndi.JndiObjectFactoryBean等。

这时，能否在尽可能少修改原有类代码下的情况下，做到动态切换不同的数据源？此时就可以用到装饰者模式。

Spring根据每次请求的不同，将dataSource属性设置成不同的数据源，以到达切换数据源的目的。

**Spring中类名中带有：Decorator和Wrapper单词的类，都是装饰器模式。**

### 观察者模式

定义对象间的一对多的关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并自动更新。Spring中观察者模式一般用在listener的实现

### 策略模式

策略模式是行为性模式，调用不同的方法，适应行为的变化 ，强调父类的调用子类的特性 。

getHandler是HandlerMapping接口中的唯一方法，用于根据请求找到匹配的处理器。

比如我们自己写了AccountDao接口，然后这个接口下有不同的实现类：AccountDaoForMySQL，AccountDaoForOracle。对于service来说不需要关心底层具体的实现，只需要面向AccountDao接口调用，底层可以灵活切换实现，这就是策略模式。

### 模板方法模式

Spring中的JdbcTemplate类就是一个模板类。它就是一个模板方法设计模式的体现。在模板类的模板方法execute中编写核心算法，具体的实现步骤在子类中完成。
