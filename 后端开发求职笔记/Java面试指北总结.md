# Java面试指北总结
[Java面试指北](https://www.yuque.com/snailclimb/mf2z3k/vfvgmz)
## 面试准备
1. 润色简历
2. 技术面试
3. 八股文
    - 基础知识点：java基础、集合、并发、mysql、redis、redis、springboot、spring
    - 项目经历涉及到的知识点
    - 分布式/高并发/微服务校招一般不会强制要求
    - 大厂会问JVM相关知识点
    - 八股文：[Java面试指北](https://www.yuque.com/snailclimb/mf2z3k/vfvgmz) [JavaGuide](https://javaguide.cn/)  
    - 算法
    - 准备自我介绍

## 暑期实习和日常实习

- 提前批：7月左右开始

## 简历
1. 简历上的内容决定面试官的提问重点
2. 简历样式
3. 简历内容
。。。具体见文章专栏

## 复习如何抓重点

## 为什么要学习源码

- 面试会的话很加分，不会也不一定被pass
- 可以先从 JDK 的几个常用集合看起。另外，我比较推荐看 Dubbo 的，因为感觉会稍微相对容易一点，模块划分清晰，注释也比较详细。
- 拿 Spring/Spring Boot 源码举例：你一定要去看 IOC 和 AOP 具体的实现，要知道一个 Spring Bean 是如何一步一步被创建出来的。一定要搞清 Spring Boot 是如何实现自动配置的。

### JDK
- 阅读源码之前，一定要先熟悉项目。你连 Dubbo 怎么使用、RPC 是个啥都不知道，就直接去看 Dubbo 源码的话，不是纯属扯淡么？
- 阅读源码之前，一定要对项目源码使用的技术有一个最基本的认识。

## 如何准备算法面试

中小厂、国企对算法要求不是很高，基本不会问
- 数据结构和算法基础：剑指offer
- 熟悉java冲用数据结构的实现 HashMap、TreeMap，TreeSet，PriorityQueue，Deque
- 不建议刷贪心法的题目
- 时间不充裕，从高频面试题开始刷/CodeTop企业题库
另外，下面这些算法专题都挺值得刷一遍的(有重复)：
    - 《剑指 Offer（专项突击版）》: https://doocs.github.io/leetcode/#/lcof2/README
    - 《程序员面试金典（第 6 版）》: https://doocs.github.io/leetcode/#/lcci/README
    - Leetcode 面试经典 150 题：https://leetcode.cn/studyplan/top-interview-150/ 
    - Leetcode 的 100 道高频算法题：https://leetcode.cn/studyplan/top-100-liked/ 
    - 牛客网面试高频 202：https://www.nowcoder.com/exam/oj?page=1&tab=算法篇&topicId=354

- [技术八股自测](https://t.zsxq.com/0eM78gbAr) 回答六七成可面试,注意参照原文关注`面试重点`
- [推荐的公司](https://github.com/csguide-dabai/Programmer-look-at-China) 

### SQL笔试题

面试考察不是很多

- 牛客网SQL刷题地址：https://www.nowcoder.com/exam/oj?page=1&tab=SQL%E7%AF%87&topicId=298 。Leetcode SQL刷题地址：https://leetcode.cn/problemset/database/ 。

- 如果想要准备算法面试但时间比较赶的话，建议优先刷这些算法题：https://t.zsxq.com/182NOhdQ5 。

## 如何积累项目经验

- 可以通过慕课网、哔哩哔哩、拉勾、极客时间、培训机构（比如黑马、尚硅谷）等渠道获取到适合自己的实战项目视频/专栏。
- 跟着教程做的过程中，你一定要有自己的思考，不要浅尝辄止
- ⭐️[Java优质开源项目](https://javaguide.cn/open-source-project/practical-project.html) 
- [awesome-java](https://github.com/CodingDocs/awesome-java) 
- 如果你想真正学到东西的话，建议不光要把项目单纯完成跑起来，还要去自己尝试着优化！几个比较容易的优化点：
  - 全局异常处理 ：很多项目这方面都做的不是很好，可以参考我的这篇文章：《使用枚举简单封装一个优雅的 Spring Boot 全局异常处理！》 来做优化。
  - 项目的技术选型优化 ：比如使用 Guava 做本地缓存的地方可以换成 Caffeine 。Caffeine 的各方面的表现要更加好！再比如 Controller 层是否放了太多的业务逻辑。
  - 数据库方面 ：数据库设计可否优化？索引是否使用使用正确？SQL 语句是否可以优化？是否需要进行读写分离？
  - 缓存 ：项目有没有哪些数据是经常被访问的？是否引入缓存来提高响应速度？
  - 安全 ： 项目是否存在安全问题？
  - ......

常见的性能优化方向实践（涉及到多线程、JVM、数据库/缓存、数据结构优化这 4 个常见的性能优化方向）总结请看：https://t.zsxq.com/0c1uS7q2Y。

- Gitee 上的 [Java项目Hub](https://gitee.com/itxinfei/hub),这个仓库总结了培训机构中常见的一些教学实战类项目，面试中用的人比较多。如果你的项目也是其中这些的话，记得一定要改一下名字，添加一些有特色的亮点。

如果你的项目属于上面列举的那种用的人比较多的类型，想要写这个项目在简历上的话，修改一个比较像真实项目的名字是必需的。另外，你需要加入一些和其他人不一样的东西，比如简单改变一下 MQ 的技术选型、优化一下原项目的某个模块的技术实现。如果完全按照原教程来写的话，很容易和别人撞车（如果已经优化过的话，可以忽略这条建议）。

- 除此之外，你还可以将这些烂大街的项目包装成其他业务类型的项目。基本原则就是：基本不改变技术实现，但对项目的业务类型进行改变。这也是很多同学用到的一个方法，还挺有效的。

- 另外， 项目已经上线或者你已经部署到服务器的话，那也是加分点。

- IDEA 优化代码的小技巧，超级实用！

分析你的代码：右键项目-> Analyze->Inspect 扫描完成之后，IDEA 会给出一些可能存在的代码问题，如命名问题。


 

