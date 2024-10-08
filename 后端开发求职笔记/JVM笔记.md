---
title: JVM
url: https://javaguide.cn/java/jvm/jvm-intro.html
date: 2024-03-25 21:32:47
tags:
- JVM
excerpt: 
index_img: /img/
mermaid: false
---

<!-- markdown-toc GFM -->

* [一、JVM基本介绍](#一jvm基本介绍)
  * [1.1 Java 文件是如何被运行的](#11-java-文件是如何被运行的)
* [二、类加载器](#二类加载器)
  * [类加载的流程](#类加载的流程)
    * [加载](#加载)
    * [链接](#链接)
    * [初始化](#初始化)
    * [卸载](#卸载)
  * [类加载器的加载顺序](#类加载器的加载顺序)
    * [双亲委派机制](#双亲委派机制)
* [运行时数据区](#运行时数据区)
  * [本地方法栈](#本地方法栈)
  * [方法区](#方法区)
  * [虚拟机栈和虚拟机堆。](#虚拟机栈和虚拟机堆)
    * [虚拟机栈的概念](#虚拟机栈的概念)
    * [虚拟机栈存在的异常](#虚拟机栈存在的异常)
    * [虚拟机栈的生命周期](#虚拟机栈的生命周期)
    * [虚拟机栈的执行](#虚拟机栈的执行)
    * [局部变量的复用](#局部变量的复用)
    * [虚拟机堆的概念](#虚拟机堆的概念)
    * [如何判断一个对象需要被干掉](#如何判断一个对象需要被干掉)
    * [如何宣告一个对象的真正死亡](#如何宣告一个对象的真正死亡)
  * [垃圾回收算法](#垃圾回收算法)
  * [各种各样的垃圾回收器](#各种各样的垃圾回收器)

<!-- markdown-toc -->
# 一、JVM基本介绍
## 1.1 Java 文件是如何被运行的
- 类加载器：.java文件被编译为.class文件，类加载器将其搬运到JVM虚拟机中运行
- 方法区：它和方法区都同属于**线程共享区域**。也就是说它们都是**线程不安全**的
- 堆：存放存储的数据，例如对象实例，数组
- 栈：代码运行的空间,一个方法来了就会被压入栈中,独享区域,
  - 程序计数器：主要就是完成一个加载工作，类似于一个指针一样的，指向下一行我们需要执行的代码

  summery: 对象实例初始化时会去方法区中找类信息，完成后再到栈那里去运行方法。找方法就在方法表中找。

# 二、类加载器
## 类加载的流程
  从类被加载到虚拟机内存中开始，到释放内存总共有 7 个步骤：加载，验证，准备，解析，初始化，使用，卸载。其中验证，准备，解析三个部分统称为连接
### 加载
  1. 将class加载到内存
  2. 将静态数据结构转化成方法区中运行时的数据结构
  3. 在堆中生成一个代表这个类的 java.lang.Class 对象作为数据访问的入口
### 链接
  1. 验证：安全检查
  2. 准备：为`static`变量在`方法区`分配内存，设置变量的初始值
  3. 解析: 虚拟机将常量池内的符号引用替换为直接引用的过程（符号引用比如我现在 import java.util.ArrayList 这就算符号引用，直接引用就是指针或者对象地址，注意引用对象一定是在内存进行）

### 初始化

  执行`类构造器`方法 <clinit>(),这个方法从父类到子类，依次执行所有static修饰的静态变量和静态代码块中的显式初始化

  - 注意：字节码文件的初始化方法有两种，非静态资源初始化：`<init>`,静态资源初始化`<clinit>`,

### 卸载

  GC将无用对象从内存中卸载

## 类加载器的加载顺序

  - BootStrap ClassLoader：rt.jar
  - Extension ClassLoader: 加载扩展的 jar 包
  - App ClassLoader：指定的 classpath 下面的 jar 包
  - Custom ClassLoader：自定义的类加载器

### 双亲委派机制

  当一个类收到加载请求时，先委派AppClassLoader去让父类加载，如果父类加载器无法完成请求，再让子类加载器加载

# 运行时数据区

## 本地方法栈 

  用`native`关键词修饰的方法称为本地方法，是用C语言实现的，这些方法都会放到`本地方法栈`区域。`程序计数器`其实就是一个指针，指向程序中下一句需要执行的命令。`字节码解析器`通过改变这个技术器的值选取下一条需要执行的字节码命令。但如果执行的是`native` 方法，那么指针就不工作了。

## 方法区

  主要作用是存放类的元数据信息，常量和静态变量等

## 虚拟机栈和虚拟机堆。
  In a word：栈管运行，堆管存储。虚拟机栈负责运行代码，虚拟机堆负责存储数据。

### 虚拟机栈的概念

  它是 Java 方法执行的内存模型。里面会对局部变量，动态链表，方法出口，栈的操作（入栈和出栈）进行存储，且`线程独享`。同时如果我们听到局部变量表，那也是在说虚拟机栈

### 虚拟机栈存在的异常
  - 如果线程请求的栈的深度大于虚拟机栈的最大深度，就会报 StackOverflowError （这种错误经常出现在递归中）

  - Java 虚拟机也可以动态扩展，但随着扩展会不断地申请内存，当无法申请足够内存时就会报错 OutOfMemoryError。

### 虚拟机栈的生命周期
  对于栈来说，不存在垃圾回收。只要程序运行结束，栈的空间自然就会释放了。栈的生命周期和所处的线程是一致的。

  这里补充一句：8 种基本类型的变量+对象的引用变量+实例方法都是在栈里面分配内存。

### 虚拟机栈的执行
  - 栈帧数据，说白了在 JVM 中叫栈帧，放到 Java 中其实就是方法，它也是存放在栈中的。

  - 栈中的数据都是以栈帧的格式存在，它是一个关于方法和运行期数据的数据集。比如我们执行一个方法 a，就会对应产生一个栈帧 A1，然后 A1 会被压入栈中。同理方法 b 会有一个 B1，方法 c 会有一个 C1，等到这个线程执行完毕后，栈会先弹出 C1，后 B1,A1。它是一个先进后出，后进先出原则。

### 局部变量的复用
  - 局部变量表用于存放`方法参数`和方法内部所定义的`局部变量`。。它的容量是以 Slot 为最小单位，一个 slot 可以存放 32 位以内的数据类型。
  - 虚拟机通过索引定位的方式使用局部变量表，范围为 [0,局部变量表的 slot 的数量]。方法中的参数就会按一定顺序排列在这个局部变量表中，至于怎么排的我们可以先不关心。而为了节省栈帧空间，这些 slot 是可以复用的，当方法执行位置超过了某个变量，那么这个变量的 slot 可以被其它变量复用。当然如果需要复用，那我们的垃圾回收自然就不会去动这些内存。

###  虚拟机堆的概念

  JVM 内存会划分为堆内存和非堆内存，堆内存中也会划分为年轻代和老年代，而非堆内存则为永久代年轻代又会分为Eden和Survivor区。Survivor 也会分为FromPlace和ToPlace，toPlace 的 survivor 区域是空的。Eden，FromPlace 和 ToPlace 的默认占比为 8:1:1。当然这个东西其实也可以通过一个 -XX:+UsePSAdaptiveSurvivorSizePolicy 参数来根据生成对象的速率动态调整。

  堆内存中存放的是对象，垃圾收集就是收集这些对象然后交给 GC 算法进行回收。

  非堆内存其实我们已经说过了，就是方法区。在 1.8 中已经移除永久代，替代品是一个元空间(MetaSpace)，最大区别是 metaSpace 是不存在于 JVM 中的，它使用的是本地内存。并有两个参数
  ```plaintext
  MetaspaceSize：初始化元空间大小，控制发生GC
  MaxMetaspaceSize：限制元空间大小上限，防止占用过多物理内存。
  ```

  ### Eden年轻代的介绍

  - 当我们 new 一个对象后，会先放到 Eden 划分出来的一块作为存储空间的内存，但是我们知道对堆内存是线程共享的，所以有可能会出现两个对象共用一个内存的情况。这里 JVM 的处理是为每个线程都预先申请好一块连续的内存空间并规定了对象存放的位置，而如果空间不足会再申请多块内存空间。这个操作我们会称作 TLAB，有兴趣可以了解一下。

  - 当 Eden 空间满了之后，会触发一个叫做 Minor GC（就是一个发生在年轻代的 GC）的操作，存活下来的对象移动到 Survivor0 区

  - 老年代是存储长期存活的对象的，占满时就会触发我们最常听说的 Full GC，期间会停止所有线程等待 GC 的完成。所以对于响应要求高的应用应该尽量去减少发生 Full GC 从而避免响应超时的问题。

  - 而且当老年区执行了 full gc 之后仍然无法进行对象保存的操作，就会产生 OOM(OutOfMemoryError,内存溢出错误)，这时候就是虚拟机中的堆内存不足，原因可能会是堆内存设置的大小过小，这个可以通过参数-Xms、-Xmx 来调整。也可能是代码中创建的对象大且多，而且它们一直在被引用从而长时间垃圾收集无法收集它们。
[示意图](https://static001.geekbang.org/infoq/39/398255141fde8ba208f6c99f4edaa9fe.png)

### 如何判断一个对象需要被干掉
[流程图](https://static001.geekbang.org/infoq/1b/1ba7f3cff6e07c6e9c6765cc4ef74997.png)
图中程序计数器、虚拟机栈、本地方法栈，3 个区域随着线程的生存而生存的。内存分配和回收都是确定的。随着线程的结束内存自然就被回收了，因此不需要考虑垃圾回收的问题。而 Java 堆和方法区则不一样，各线程共享，内存的分配和回收都是动态的。因此垃圾收集器所关注的都是堆和方法这部分内存。

在进行回收前就要判断哪些对象还存活，哪些已经死去。下面介绍两个基础的计算方法
1. 引用计数器计算：给对象添加一个引用计数器，每次引用这个对象时计数器加一，引用失效时减一，计数器等于 0 时就是不会再次使用的。不过这个方法有一种情况就是出现对象的循环引用时 GC 没法回收。
2. 可达性分析计算：这是一种类似于二叉树的实现，将一系列的 GC ROOTS 作为起始的存活对象集，从这个节点往下搜索，搜索所走过的路径成为引用链，把能被该集合引用到的对象加入到集合中。搜索当一个对象到 GC Roots 没有使用任何引用链时，则说明该对象是不可用的。主流的商用程序语言，例如 Java，C#等都是靠这招去判定对象是否存活的。

（了解一下即可）在 Java 语言汇总能作为 GC Roots 的对象分为以下几种：虚拟机栈（栈帧中的本地方法表）中引用的对象（局部变量）方法区中静态变量所引用的对象（静态变量）方法区中常量引用的对象本地方法栈（即 native 修饰的方法）中 JNI 引用的对象（JNI 是 Java 虚拟机调用对应的 C 函数的方式，通过 JNI 函数也可以创建新的 Java 对象。且 JNI 对于对象的局部引用或者全局引用都会把它们指向的对象都标记为不可回收）已启动的且未终止的 Java 线程这种方法的优点是能够解决循环引用的问题，可它的实现需要耗费大量资源和时间，也需要 GC（它的分析过程引用关系不能发生变化，所以需要停止所有进程）

###  如何宣告一个对象的真正死亡
finalize()是 Object 类的一个方法、一个对象的 finalize()方法只会被系统自动调用一次，经过 finalize()方法`逃脱死亡`的对象，第二次不会再调用。

补充一句：并不提倡在程序中调用 finalize()来进行自救。建议忘掉 Java 程序中该方法的存在。因为它执行的时间不确定，甚至是否被执行也不确定（Java 程序的不正常退出），而且运行代价高昂，无法保证各个对象的调用顺序（甚至有不同线程中调用）。在 Java9 中已经被标记为 deprecated ，且 java.lang.ref.Cleaner（也就是强、软、弱、幻象引用的那一套）中已经逐步替换掉它，会比 finalize 来的更加的轻量及可靠。

判断一个对象的死亡至少需要两次标记

1. 如果对象进行可达性分析之后没发现与 GC Roots 相连的引用链，那它将会第一次标记并且进行一次筛选。判断的条件是决定这个对象是否有必要执行 finalize()方法。如果对象有必要执行 finalize()方法，则被放入 F-Queue 队列中。

2. GC 对 F-Queue 队列中的对象进行二次标记。如果对象在 finalize()方法中重新与引用链上的任何一个对象建立了关联，那么二次标记时则会将它移出“即将回收”集合。如果此时对象还没成功逃脱，那么只能被回收了。

## 垃圾回收算法

## 各种各样的垃圾回收器
[HotSpot中的垃圾回收器以及适用场景](https://static001.geekbang.org/infoq/9f/9ff72176ab0bf58bc43e142f69427379.png)

到 jdk8 为止，默认的垃圾收集器是 Parallel Scavenge 和 Parallel Old从 jdk9 开始，G1 收集器成为默认的垃圾收集器 目前来看，G1 回收器停顿时间最短而且没有明显缺点，非常适合 Web 应用。在 jdk8 中测试 Web 应用，堆内存 6G，新生代 4.5G 的情况下，Parallel Scavenge 回收新生代停顿长达 1.5 秒。G1 回收器回收同样大小的新生代只停顿 0.2 秒。


