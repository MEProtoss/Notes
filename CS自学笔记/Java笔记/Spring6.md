2023/11/21 11:06:16

# Spring

- Spring其实就是一个管理Bean对象的工厂

流程

- [ ] 添加注解 将类纳入spring管理。
- [ ]

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

### Bean的作用

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

- 它是一个Bean，是一个能够辅助Spring实例化其它Bean对象的一个Bean。
  在Spring中，Bean可以分为两类：
  ● 第一类：普通Bean
  ● 第二类：工厂Bean（记住：工厂Bean也是一种Bean，只不过这种Bean比较特殊，它可以辅助Spring实例化其它Bean对象。）

### 注入自定义 Date (工厂Bean的实际应用)

### Bean 的生命周期(可分为5步7步10步)

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

- [ ] Spring只能解决setter方法注入的单例bean之间的循环依赖。ClassA依赖ClassB，ClassB又依赖ClassA，形成依赖闭环。Spring在创建ClassA对象后，不需要等给属性赋值，直接将其曝光到bean缓存当中。在解析ClassA的属性时，又发现依赖于ClassB，再次去获取ClassB，当解析ClassB的属性时，又发现需要ClassA的属性，但此时的ClassA已经被提前曝光加入了正在创建的bean的缓存中，则无需创建新的的ClassA的实例，直接从缓存中获取即可。从而解决循环依赖问题。

## 回顾反射机制

### 方法调用的四个要素

- 哪个对象
- 哪个方法
- 哪个参数
- 返回什么值

## 全注解式开发

- @Configuration
- @ConponentScan

### 负责注入的注解

- @Value 负责注入简单类型

- @Autowired 单独使用@Autowired注解，默认根据类型装配。【默认是byType】

- 配合@Qualified使用才能byName进行装配

- @Resource注解默认根据属性名进行装配。

## GOF代理模式

- [ ] 静态代理
  > > - [ ]
- [ ] 动态代理

## "面向切面编程的AOP"

- [ ] 用一句话总结AOP：将与核心业务无关的代码独立的抽取出来，形成一个独立的组件，然后以横向交叉的方式应用到业务流程当中的过程被称为AOP。

### AOP的优点

- 第一：代码复用性增强。
- 第二：代码易维护。
- 第三：使开发者更关注业务逻辑。

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

### 切点表达式

```java
execution([访问控制权限修饰符] 返回值类型 [全限定类名]方法名(形式参数列表) [异常])
```

### 使用Spring的AOP

### 切面的先后顺序

- [ ] 可以使用@Order注解来标识切面类，为@Order注解的value指定一个整数型的数字，数字越小，优先级越高。

```java
@Order(1) //设置优先级
```

### 通用切点

- 将切点表达式单独的定义出来，在需要的位置引入即可

### 连接点(Joinpoint)

- [ ] getSignature 获取目标方法的签名

```java
public 开始一直到{}之前
```

### 全注解开发

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

# Spring6整合JUnit5

## Spring对JUnit4的支持

:wq
Spring提供的方便主要是这几个注解：

- @RunWith(SpringJUnit4ClassRunner.class)
- @ContextConfiguration("classpath:spring.xml")

- 在单元测试类上使用这两个注解之后，在单元测试类中的属性上可以使用@Autowired。比较方便。

## Spring对JUnit5的支持

在JUnit5当中，可以使用Spring提供的以下两个注解，标注到单元测试类上，这样在类当中就可以使用@Autowired注解了。

- @ExtendWith(SpringExtension.class)
- @ContextConfiguration("classpath:spring.xml")

# Spring6集成MyBatis3.5

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
