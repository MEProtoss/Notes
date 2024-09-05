# Java基础总结

## 第一章 Java语言概述

- practice typing

### Java technology system platform

- Java SE (Standard Edition)
- Java EE (Enterprise Edition)
- Java ME (Micro Edition)

### JDK,JRE

- JDK (`J`ava `D`evelopment `K`it):：是Java程序开发工具包，包含`JRE` 和开发人员使用的工具。

- JRE (`J`ava `R`untime `E`nvironment) ：是Java程序的运行时环境，包含`JVM` 和运行时所需要的`核心类库`。

![image20220310200731185](file:///home/time/编程学习/Java/01_课件与电子教材/尚硅谷_第01章_Java语言概述/images/image-20220310200731185.png?msec=1699579156372)

> 小结：
>
> JDK = JRE + 开发工具集（例如Javac编译工具等）
>
> JRE = JVM + Java SE标准类库

### 配置path环境变量

- Configure path environment variables

- 什么是path环境变量？
  答：window操作系统执行命令时，所要搜寻的路径。

- [ ] how to configure path environments on linux?

### Java开发的三个步骤

- 编写.java
- javac.exe 编译->.class
- java.exe运行 -> result

### grammatical problem

- 声明为public的类应与文件名一致，否知编译失败。

### 源文件与类名

- 不管是否是public，都与源文件名保持一致，而且一个源文件尽量只写一个类，目的是为了好维护。

### Comment

- **文档注释内容可以被JDK提供的工具 javadoc 所解析，生成一套以网页文件形式体现的该程序的说明文档。**

```
javadoc -d mydoc -author -version HelloWorld.java
```

### API(Application Programming Interface)

- Java API文档，即为JDK使用说明书、帮助文档。

### JVM (Java Virtual Machine)

- 原理：只要在需要运行 java 应用程序的操作系统上，先安装一个Java虚拟机 (`J`VM ，Java `V`irtual `M`achine) 即可。由JVM来负责Java程序在该系统中的运行。

- 面向对象 -> 实现高内聚 低耦合。

## 第2章 变量与运算符 (Variables and Operators)

### 关键字 keywords

String used for specialized purposes

- `class` `public` `static` `void` etc. **全都小写**

### 标识符(identifier)

Java中变量、方法、类等要素命名时使用的字符序列，称为标识符。
技巧：**凡是自己可以起名字的地方都叫标识符**。

- can not begin with nums

#### Naming conventions

> 包名：多单词组成时所有字母都小写：xxxyyyzzz。
> 例如：java.lang、com.atguigu.bean

> 类名、接口名：多单词组成时，所有单词的首字母大写：XxxYyyZzz
> 例如：HelloWorld，String，System等

> 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
> 例如：age,name,bookName,main,binarySearch,getName

> 常量名：所有字母都大写。多单词时每个单词用下划线连接：XXX_YYY_ZZZ
> 例如：MAX_VALUE,PI,DEFAULT_CAPACITY

注意：在起名字时，为了提高阅读性，要尽量有意义，“见名知意”。

> 更多细节详见《代码整洁之道\_关于标识符.txt》《阿里巴巴Java开发手册-1.7.1-黄山版》

### 变量的数据类型 The data type of the variable

- **基本数据类型**：包括 `整数类型`、`浮点数类型`、`字符类型`、`布尔类型`。
- **引用数据类型**：包括`数组` array、 `类` class 、`接口` interface 、`枚举` enum (enumeration)、`注解`(annotation)、`记录`(record)。

- char类型是可以进行运算的。因为它都对应有Unicode码，可以看做是一个数值

字符型变量的三种表现形式：

- **形式1：** 使用单引号(' ')括起来的`单个字符`。

  例如：char c1 = 'a'; char c2 = '中'; char c3 = '9';

- **形式2：** 直接使用 `Unicode值`来表示字符型常量：‘`\uXXXX`’。其中，XXXX代表一个十六进制整数。

  例如：\u0023 表示 '#'。

- **形式3：** Java中还允许使用`转义字符‘\’`来将其后的字符转变为特殊字符型常量。

  例如：char c3 = '\n'; // '\n'表示换行符

### 基本类型之间的运算

- 自动类型提升 小 -> 大
- 强制类型转换 大 -> 小

- [ ] 当byte,short,char数据类型的变量进行算术运算时，按照int类型处理

### 运算符

- 左移:<<

- [ ] 运算规则：在一定范围内，数据每向左移动一位，相当于原数据\*2。（正数、负数都适用）

【注意】当左移的位数n超过该数据类型的总位数时，相当于左移（n-总位数）位

- 右移 : >>

- [ ] 相当于/2

### ASCII

`A` :65

## 第3章 流程控制语句 control float statement

### 循环语句

- 生成一个[a,b] 范围的随机数的方式：(int)(Math.random() \* (b - a + 1) + a)

  - Scanner 类的使用

  ```java
  import java.util.Scanner;
  ```

  ```java
  Scanner input = new Scanner(System.in);
  num = input.nextInt();
  int num = 1; //初始化为特殊值，使得第一次循环条件成立
  input.close();

  ```

- 在switch语句中，\*\*如果case的后面不写break，将出现穿透现象，也就是一旦匹配成功，不会在判断下一个case的值，直接向后运行，直到遇到break或者整个switch语句结束，执行终止。

### 3.4 对比三种循环结构

- **从循环次数角度分析**
- do-while循环至少执行一次循环体语句。
- for和while循环先判断循环条件语句是否成立，然后决定是否执行循环体。

- **如何选择**
- 遍历有明显的循环次数（范围）的需求，选择for循环
- 遍历没有明显的循环次数（范围）的需求，选择while循环
- 如果循环体语句块至少执行一次，可以考虑使用do-while循环
- 本质上：三种循环之间完全可以互相转换，都能实现循环的功能

### 3.6 嵌套循环（或多重循环）

实质上，`嵌套循环就是把内层循环当成外层循环的循环体`。只有当内层循环的循环条件为false时，才会完全跳出内层循环，才可结束外层的当次循环，开始下一次的外层循环。

- 设外层循环次数为`m`次，内层为`n`次，则内层循环体实际上需要执行`m*n`次。
- **技巧：**从二维图形的角度看，外层循环控制`行数`，内层循环控制`列数`。
- **开发经验：**实际开发中，我们最多见到的嵌套循环是两层。一般不会出现超过三层的嵌套循环。如果将要出现，一定要停下来重新梳理业务逻辑，重新思考算法的实现，控制在三层以内。否则，可读性会很差。

- 打印菱形

```java
public class ForForTest4 {

  public static void main(String[] args) {
    /*
       上半部分        i        m(表示-的个数)    n(表示*的个数)关系式：2*i + m = 10 --> m = 10 - 2*i
       --------*           1       8               1                            n = 2 * i - 1
       ------* * *           2       6               3
       ----* * * * *       3       4               5
       --* * * * * * *       4       2               7
     * * * * * * * * *  5       0               9

     下半部分         i      m                n              关系式： m = 2 * i
     --* * * * * * *    1       2                7                     n = 9 - 2 * i
     ----* * * * *      2       4                5
     ------* * *        3       6                3
     --------*          4       8                1

     */
    //上半部分
    for (int i = 1; i <= 5; i++) {
      //-
      for (int j = 1; j <= 10 - 2 * i; j++) {
        System.out.print(" ");
      }
      //*
      for (int k = 1; k <= 2 * i - 1; k++) {
        System.out.print("* ");
      }
      System.out.println();
    }
    //下半部分
    for (int i = 1; i <= 4; i++) {
      //-
      for (int j = 1; j <= 2 * i; j++) {
        System.out.print(" ");
      }

      //*
      for (int k = 1; k <= 9 - 2 * i; k++) {
        System.out.print("* ");
      }
      System.out.println();
    }
  }

}
```

关键字break和continue后面不能声明语句

### 无限循环 infinite loop

**语法格式：**

- 最简单"无限"循环格式：`while(true)` , `for(;;)`

**适用场景：**

- 开发中，有时并不确定需要循环多少次，需要根据循环体内部某些条件，来控制循环的结束（使用break）。
- 如果此循环结构不能终止，则构成了死循环！开发中要避免出现死循环。

### break Vs continue

- [ ] break 退出当前循环结构 （大括号{}）
- [ ] continue 退出当次循环

### 带标签的循环 label

- continue语句出现在多层嵌套的循环语句体中时，也可以通过标签指明要跳过的是哪一层循环。
- 标号语句必须紧接在循环的头部。标号语句不能用在非循环语句的前面。

```java
class BreakContinueTest2 {
    public static void main(String[] args) {
        l:for(int i = 1;i <= 4;i++){

            for(int j = 1;j <= 10;j++){
                if(j % 4 == 0){
                    //break l;
                    continue l;
                }
                System.out.print(j);
            }
            System.out.println();
        }
    }
}
```

### 获取随机数

```java
/*
如何获取一个随机数?

1. 可以使用Java提供的API:Math类的random()
2. random()调用以后，会返回一个[0.0,1.0)范围的double型的随机数

3. 需求1：获取一个[0,100]范围的随机整数？
   需求2：获取一个[1,100]范围的随机整数？

4. 需求：获取一个[a,b]范围的随机整数？
   (int)(Math.random() * (b - a + 1)) + a
*/

```

## 第4章 IDEA的安装和使用

### 工程和模块管理

- [ ] project(工程) --> module(模块) --> package(包) --> class(类)
  - [ ] 注意命名规则
  - [ ] 包取名一般是公司域名倒着写

## 第5章 数组 array

- [ ] 有序 一次紧密排列 可重复 长度一旦确定就不能修改
- [ ] 引用类型的数组每个元素存放的是变量的地址

### 一维数组内存解析

- [ ] 方法栈存放局部变量和方法
- [ ] 堆存放new 新建的对象

### Arrays 工具类

- [ ] java.util.Arrays类即为操作数组的工具类，包含了用来操作数组（比如排序和搜索）的各种方法。
  > > - [ ] 熟悉一下内部的常用的方法
  > > > - [ ] toString() / sort() / binarySearch()

## 第6章 面向对象编程 (Object Oriented Programming)

### 对象的内存解析

- [ ] 堆（Heap） ：此内存区域的唯一目的就是存放对象实例，几乎所有的对象实例都在这里分配内存。这一
      点在Java虚拟机规范中的描述是：所有的对象实例以及数组都要在堆上分配。

- [ ] 栈（Stack） ：是指虚拟机栈。

  > > - [ ] 虚拟机栈用于存储局部变量等。局部变量表存放了编译期可知长度的各
  > >       种基本数据类型（boolean、byte、char、short、int、float、long、double）、对象引用（reference类
  > >       型，它不等同于对象本身，是对象在堆内存的首地址）。 方法执行完，自动释放。

- [ ] 方法区（Method Area） ：用于存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。

---

- 说明：
- [ ] 堆：凡是new出来的结构(对象、数组)都放在堆空间中。
- [ ] 对象的属性存放在堆空间中。
- [ ] 创建一个类的多个对象（比如p1、p2），则每个对象都拥有当前类的一套"副本"（即属
      性）。当通过一个对象修改其属性时，不会影响其它对象此属性的值。
- [ ] 当声明一个新的变量使用现有的对象进行赋值时（比如p3 = p1），此时并没有在堆空间中创
      建新的对象。而是两个变量共同指向了堆空间中同一个对象。当通过一个对象修改属性时，
      会影响另外一个对象对此属性的调用。

### 方法的重载(overload)

- [ ] 同名但是不同参数列表 Same name but different parameter list

### variable number of arguments

- [ ] format

```java
方法名(参数的类型名 ...参数名)
```

- [ ] 方法的参数部分有可变形参，需要放在形参声明的最后
- [ ] 在一个方法的形参中，最多只能声明一个可变个数的形参

### parameter passing: pass-by-value

- [ ] 形参是基本数据类型：将实参基本数据类型变量的“数据值”传递给形参
- [ ] 形参是引用数据类型：将实参引用数据类型变量的“地址值”传递给形参

### 递归recursion

### 关键字：package import

- [ ] 包用于指明该文件中定义的类，接口等所在的包

  > > - [ ] package语句作为Java源文件的第一条语句出现。若缺省该语句，则指定为无名包。
  > > - [ ] 同一个包下不能定义同名的结构

- [ ] 为了使用定义在其它包中的Java类，需用import语句来显式引入指定包下所需要的类。相当于 import语
      句告诉编译器到哪里去寻找这个类 。

```java
import 包名.类名;
```

### 封装性(encapsulation)

- [ ] 本类内部 本包内 其他包的子类 其他包非子类

- [ ] private protected 缺省 public

### JavaBean

- [ ] Three conditions
  > > - [ ] the class is public
  > > - [ ] have a constructor with no parameter
  > > - [ ] have fields and their "set-get" methods

## 第7章

### this

- [ ] this关键字如果再本类中未找到 会继续从父类中找
- [ ] 可以调用本类中的无参构造器和有参构造器

```java
this()
this(实参列表)
```

### 继承Inheritance

### 方法的重写 overwrite/override

- [ ] 子类对父类继承自父类的方法进行改造
  > > - [ ] 子类重写的方法必须和父类具有相同的方法名和参数列表
  > > - [ ] 方法的返回值类型不能大于父类的，如果是void 则必须相同
  > > - [ ] 访问权限不能小于父类

### super

- [ ] 父类的

- [ ] 开发中常见错误：

> > - [ ] 如果子类构造器中既未显式调用父类或本类的构造器，且父类中又没有空参的构造器，则`编译出错`。

### 多态性 polymorphism

- [ ] 父类的引用指向子类的对象

```java
父类类型 变量名 = 子类对象
```

- [ ] 编译看左边 运行看右边

### 类型转换

- [ ] 父类 --> instanceof --> 子类

```java
//检验对象a是否是数据类型A的对象，返回值为boolean型
对象a instanceof 数据类型A

```

- [ ] 说明：

> > - [ ] 只要用instanceof判断返回true的，那么强转为该类型就一定是安全的，不会报ClassCastException异常。
> > - [ ] 如果对象a属于类A的子类B，a instanceof A值也为true。
> > - [ ] 要求对象a所属的类与类A必须是子类和父类的关系，否则编译错误。

- [ ] 子类 -> 父类 (自动向上转型)

### object 类中的方法

- [ ] eaquls和==的区别
  > > - [ ] == 既可以比较基本类型也可以比较引用类型。对于基本类型就是比较值，对于引用类型就是比较内存地址
  > > - [ ] equals的话，它是属于java.lang.Object类里面的方法，如果该方法没有被重写过默认也是==;日常开发中一般会重写该方法使其用来比较值
- [ ] toString()
  > > - [ ] 默认情况下，toString()返回的是“对象的运行时类型 @ 对象的hashCode值的十六进制形式"
  > > - [ ] 在进行String与其它类型数据的连接操作时，自动调用toString()方法
  > > - [ ] 日常开发一般会重写该方法以获得当前对象的属性信息

### getClass()

- [ ] 获取对象的运行时类型
  > > - [ ] 因为Java有多态现象，所以一个引用数据类型的变量的编译时类型与运行时类型可能不一致，因此如果需要查看这个变量实际指向的对象的类型，需要用getClass()方法

### hashCode()

- [ ] 获取对象的hash值

## 第8章 面向对象高级

### static

- [ ] 随着类的加载而加载，可以直接由类调用

- [ ] 静态方法内部只能访问类的static修饰的属性或方法。
- [ ] 静态方法可以被子类继承，但不能被子类重写

### 单例设计模式

- [ ] 类在一个虚拟机中只能产生一个对象

- 饿汉式(提前在类中创建好对象，可直接调用)
  > > - [ ] 将类的构造器权限设置为private
  > > - [ ] 内部提供一个当前类的实例，且必须静态(static) ，因为要随着类的加载而加载。
  > > - [ ] 提供公共的静态的方法，返回当前类的对象
- 懒汉式(在类中对对象进行私有化声明但是并不创建，在公共的静态方法中创建对象，这样的话类加载的时候对象并没有创建，仅仅在该方法被调用时才会创建对象)
  > > - [ ] 将类的构造器权限设置为private
  > > - [ ] 内部提供一个当前类对象的声明，且必须静态(static) ，因为要随着类的加载而加载。
  > > - [ ] 提供公共的静态的方法，创建并返回对象

_注意：在多线程中，不能使用懒汉式，因为多个线程可能创建多个对象，线程不安全，不能保证单例的唯一性_

### 静态代码块

- [ ] 用于初始化静态变量(属性，类的声明)
- [ ] 静态代码块里不能调用非静态结构
- [ ] 多个静态代码块从上到下依次执行
- [ ] 随着类的加载而加载，执行优先于非静态代码块

### 非静态代码块

- [ ] 用于初始化实例变量
- [ ] 如果多个重载的构造器有公共代码，并且这些代码都是先于构造器其他代码执行的，那么可以将这部分代码抽取到非静态代码块中，减少冗余代码。
- [ ] 每次创建对象都会执行一次，先于构造器执行

### final关键字

- [ ] 最终的 不可更改的

### 抽象类 abstract

```java
[权限修饰符] abstract class 类名{

}
[权限修饰符] abstract class 类名 extends 父类{

}
```

- [ ] 没有方法体，必须由子类重写
- [ ] 包含抽象方法的类必须是抽象类
- [ ] 抽象类就使用来被继承的！！
- [ ] 抽象类不能创建对象，子类重写所有抽象方法再创建对象

### 接口 Interface ---------突出一个`公共`

- [ ] 接口就是一种规范，定义对象中公共的东西，接口不是类，接口可以理解为一种`必须`,接口仅仅提供方法的签名，不提供实现
      `

```java
[修饰符] interface 接口名{
      //接口的成员列表：
      // 公共的静态常量
      // 公共的抽象方法

      // 公共的默认方法（JDK1.8以上）
      // 公共的静态方法（JDK1.8以上）
      // 私有方法（JDK1.9以上）
  }
```

- [ ] 接口中没有构造器，没有初始化块(代码块)，因为接口中没有成员变量需要动态初始化

- [ ] 如果实现类不是抽象类，实现类必须实现接口中所有的抽象方法

- [ ] 接口间也有继承关系

### 内部类

- [ ] 成员内部类
- [ ] 就是供一个类内部调用的，通过是否要使用外部类的非静态成员判断是声明成静态的还是非静态的
- [ ] 成员内部类可以直接使用外部类的所有成员，包括私有的数据
- [ ] 可以通过外部类调用内部类的成员

### enun 枚举类

- [ ] 类的对象是有限的固定的几个，需要用的时候注意定义方法就行

### 包装类

- [ ] 基本数据类型和引用类型之间的转化,将基本数据类型封装从而就有了类的特点

- [ ] 基本数据类型-> 字符串

```java
int a = 10;
String str = a + "";
```

- [ ] 字符串 -> 基本数据类型

  > > - [ ] 想变成什么类型就去什么类型里找`parseXxx`方法

- [ ] 包装类有不少方法，将基本数据类型变成包装类之后就可以调方法进行各种操作

## 第9章 异常处理 exception handling

- [ ] 异常不是语法错误和逻辑错误
- [ ] 异常的根父类 `java.lang.Throwable`
- [ ] 异常又分为`Exception` 和 `error`
      ![1562771528807](/home/time/编程学习/Java/01_课件与电子教材/尚硅谷_第09章_异常处理/images/1562771528807.png)

- [ ] Place the statements that must be executed in `final`

### 第10章 多线程 MultiThreading

- [ ] program - process - thread
- [ ] 并行 parallel 同一时刻同时发生
- [ ] 并发 concurrency 同一时间段内快速轮换 交替执行 看上去像是同时执行

### creat and start thread

- [ ] Method 1 继承Thread类

- 定义Thread的子类->overwrite `run()`->create the instance->instance.start()

- [ ] Method 2 实现Runnable接口

- 定义`Runnable` 的实现类 -> override `run()` -> create the instance and use the instance as the target parameter of `Thread` object, which is the true thread object -> calling the start() method of a thread object

### 多线程的声明周期

![image-20220524203355448](/home/time/编程学习/Java/01_课件与电子教材/尚硅谷_第10章_多线程/images/image-20220524203355448.png)

- [ ] 线程安全问题

- several threads access the same resource at the same time ,当多个线程对资源有读和写操作的时候就容易出现问题

### 同步机制 synchronized

- [ ] 在任何时候,最多允许一个线程拥有`同步锁`，谁拿到锁就进入代码块，其他的线程只能在外等着(BLOCKED)。
  > > - [ ] 同步代码块 synchronized 关键字可以用于某个区块前面，表示只对这个区块的资源实行互斥访问。

```java
synchronized(同步锁){
     需要同步操作的代码
}
```

> > - [ ] 同步方法 synchronized 关键字直接修饰方法，表示同一时刻只有一个线程能进入这个方法，其他线程在外面等着。

```java
public synchronized void method(){
    可能会产生线程安全问题的代码
}
```

- [ ] ArrayIndexOutOfBoundsException。数组角标越界异常
  > > - [ ] 当访问数组元素时，下标指定超出[0, 数组名.length-1]的范围时，就会报数组，如果下标越界异常
- [ ] NullPointerException 空指针异常
  > > - [ ] 引用型数组的某个位置上的元素还未赋值（null）时，如果调用这个位置上的元素，就会报空指针异常

## 第8章

- 继承
  继承时不能直接访问私有属性
- 在声明一个类但没有显示写构造器的时候,会默认存在一个空参构造器，而任何一个构造器的首行。要么是this(形参列表)调用本类中其他构造器,要么是super(形参列表)调用父类指定的构造器
- 重写
  方法重写时通常直接copy 仅仅修改方法体
- super
  在子类中继续使用父类中被重写的方法
  super 可理解为 _父类的_

### equals()

- 任何引用数据类型都能使用,默认比较两个对象的引用地址

- 对于像String、File、Date和包装类等，它们都重写了Object类中的equals()方法，用于比较两个对象的实体内容是否相等。

### 代码块

- 非静态代码块在对象创建时加载，所以不同构造器里相同的代码可以统一放在代码块里。

### abstract关键字

## 第8章

### 接口(interface)

- 可以省略public static final / public abstract /

- 类是用来实现接口的 (implement)

  - 可以多实现 ，也可以先继承再实现

- 接口间可以多继承(extends)

  - 接口具有多态性

  接口名 变量名 = new 实现类的对象

### 内部类

## 异常处理

### 1. 异常概述(exception)

#### 1.3 异常的抛出机制

- 将异常用类表示，一旦发生异常,就创建类的对象，并且抛出（throw）让程序员捕获（catch）

### 2.Java异常体系

#### 2.2 错误和异常error and exception

#### 2.3编译时异常和运行时异常

- 编译时异常也称为受检异常（checked error)
- 运行时异常也称为非受检异常(uncheked error)

### 3.常见的错误和异常

#### 3.1Error

VirtualMachineError的两个经典子类：StackOverError OutOfMemoryError

#### 3.2运行时异常

- 空指针异常(NullPoint)
- 类转换异常(ClassCast)
- 数组角标越界(ArrayIndexOutOfBounds)
- 输入不匹配(InputMissMatch)

#### 3.3编译时异常

- ClassNotFound
- SQLException
- FileNotFound
- IOException

### 4.异常处理

异常处理的两种方式

- try-catch-finally（解决）
- throws + 异常类型(抛给别人)

#### 4.2捕获异常语法

```java
try{
  ......    //可能产生异常的代码
}
catch( 异常类型1 e ){
......    //当产生异常类型1型异常时的处置措施
}
catch( 异常类型2 e ){
......     //当产生异常类型2型异常时的处置措施
}
finally{
...... //无论是否发生异常，都无条件执行的语句
}

```

finally语句和catch语句是可选的,但是finally不能单独使用

#### 4.3 throws的基本格式

```java
public void readFile(String file)  throws FileNotFoundException,IOException {
  ...
    // 读文件的操作可能产生FileNotFoundException或IOException类型的异常
    FileInputStream fis = new FileInputStream(file);
  //...
}
```

- throws使用举例
- 编译时异常

```java
package com.atguigu.keyword;

public class TestThrowsCheckedException {
  public static void main(String[] args) {
    System.out.println("上课.....");
    try {
      afterClass();//换到这里处理异常
    } catch (InterruptedException e) {
      e.printStackTrace();
      System.out.println("准备提前上课");
    }
    System.out.println("上课.....");
  }

  public static void afterClass() throws InterruptedException {
    for(int i=10; i>=1; i--){
      Thread.sleep(1000);//本来应该在这里处理异常
      System.out.println("距离上课还有：" + i + "分钟");
    }
  }
}
```

- 运行时异常

```java
package com.atguigu.keyword;

import java.util.InputMismatchException;
import java.util.Scanner;

public class TestThrowsRuntimeException {
  public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    try {
      System.out.print("请输入第一个整数：");
      int a = input.nextInt();
      System.out.print("请输入第二个整数：");
      int b = input.nextInt();
      int result = divide(a,b);
      System.out.println(a + "/" + b +"=" + result);
    } catch (ArithmeticException | InputMismatchException e) {
      e.printStackTrace();
    } finally {
      input.close();
    }
  }/

  public static int divide(int a, int b)throws ArithmeticException{
    return a/b;
  }
}
```

#### 4.4 方法重写中throws的要求

```
（1）方法名必须相同
（2）形参列表必须相同
（3）返回值类型
- 基本数据类型和void：必须相同
- 引用数据类型：<=
（4）权限修饰符：>=，而且要求父类被重写方法在子类中是可见的
（5）不能是static，final修饰的方法
```

此外，对于throws异常列表要求：

- 如果父类被重写方法的方法签名后面没有 “throws 编译时异常类型”，那么重写方法时，方法签名后面也不能出现“throws 编译时异常类型”。
- 如果父类被重写方法的方法签名后面有 “`throws 编译时异常类型`”，那么重写方法时，throws的编译时异常类型必须 <= 被重写方法throws的编译时异常类型，或者不throws编译时异常。
- 方法重写，对于“`throws 运行时异常类型`”没有要求。

## 多线程

- 懒汉式vs饿汉式
  懒汉式和饿汉式是两种常见的单例设计模式，用于确保一个类只有一个实例。

懒汉式单例模式：
懒汉式是一种延迟加载的方式，它在需要的时候才创建单例对象。懒汉式的实现有两种方式：

a. 线程不安全的懒汉式：
这种方式在多线程环境下可能会创建多个实例，因为没有进行线程同步。一般不推荐使用这种方式。

```java
public class LazySingleton {
  private static LazySingleton instance;

  private LazySingleton() {}

  public static LazySingleton getInstance() {
    if (instance == null) {
      instance = new LazySingleton();
    }
    return instance;
  }
}
```

b. 线程安全的懒汉式：
这种方式通过使用同步锁（synchronized）来确保在多线程环境下只创建一个实例。但它的性能会有所下降，因为每次获取实例都需要进行同步操作。

```java
public class ThreadSafeLazySingleton {
  private static ThreadSafeLazySingleton instance;

  private ThreadSafeLazySingleton() {}

  public static synchronized ThreadSafeLazySingleton getInstance() {
    if (instance == null) {
      instance = new ThreadSafeLazySingleton();
    }
    return instance;
  }
}
```

饿汉式单例模式：
饿汉式是一种在类加载时就创建单例对象的方式，因此在多线程环境下不会出现多个实例的问题。它的缺点是如果单例对象很大或者在加载时做了很多工作，会导致性能问题。

```java
public class EagerSingleton {
  private static final EagerSingleton instance = new EagerSingleton();

  private EagerSingleton() {}

  public static EagerSingleton getInstance() {
    return instance;
  }
}
```

需要根据具体需求和性能要求来选择懒汉式或饿汉式单例模式。懒汉式可以延迟实例化，但需要考虑线程安全性，而饿汉式在类加载时就创建实例，线程安全，但可能引发性能问题。

### 静态方法不能使用关键字this

因为this关键字是用来引用当前对象（实例）的引用，而静态方法与特定的对象实例无关，它属于整个类而不是类的实例。在静态方法内部，没有隐式的this引用可用。

静态方法不与任何特定的对象实例相关联，因此在静态方法中不能访问实例变量或实例方法，因为它们通常需要一个特定的对象实例来操作。静态方法只能访问静态成员（静态变量和静态方法），因为它们是类级别的，而不是实例级别的。

如果在静态方法中需要访问实例变量或实例方法，你需要传递一个对象实例作为参数，然后使用该参数来访问实例成员，或者在静态方法内部创建一个对象实例来访问实例成员。这是因为静态方法没有默认的this引用，它们不知道要操作哪个对象的实例。

### java中while(true)

在Java中，while(true) 是一个循环结构，表示一个无限循环。它的含义是，循环条件永远为真，因此循环将一直执行下去，直到显式地使用 break 。这种循环通常用于需要无限执行的情况，例如服务器程序等，以便持续监听或处理请求。

- java 中的区间都是左闭右开
- 参数传递机制
  引用数据类型传地址，基本数据类型传数据

### 泛型

###

#### 使用场景

当我们声明一个变量/形参时，这个变量/形参的类型是一个泛型类或泛型接口，例如：Comparator<T>类型，但是我们仍然无法确定这个泛型类或泛型接口的类型变量<T>的具体类型，此时我们考虑使用类型通配符 ? 。

- <E> 写在返回值类型前才是泛型方法
- 通配符类型只能读,不能写 因为不知道类型，所以将任意元素加入到其中是类型不安全的
- 不能用在泛型方法声明上，返回值类型前面<>不能使用?
- 不能用在泛型类的声明上
- 不能用在创建对象上

### FILE类

- 任何一个file对象对应于一个文件或者一个文件目录

### 反射
