---
title: Java面试常见问题
url: Java面试常见问题
date: 2024-03-28 09:37:40
tags: [Java]
excerpt: 
index_img: /img/
mermaid: false
---
# Java
## 基础
###  基本数据类型/对应的包装类/各自占用多少字节

### String、StringBuffer、StringBuilder的区别是什么，String为什么是不可变的
- 从可变性上来说:
    - String 是不可变的。
    - 而StringBuilder 与 StringBuffer 都继承自 AbstractStringBuilder 类，在 AbstractStringBuilder 中也是使用字符数组保存字符串，不过没有使用 final 和 private 关键字修饰，最关键的是这个 AbstractStringBuilder 类还提供了很多修改字符串的方法比如 append 方法,所以是可变的

- 从线程安全性上来说
    - String 中的对象是不可变的，也就可以理解为常量，线程安全
    - StringBuffer和StringBuilder继承自AbstractStringBuilder，它定义了一些字符串的基本操作，如 expandCapacity(扩容)、append、insert、indexOf 等公共方法。而StringBuffer 对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的。
    - StringBuilder 并没有对方法进行加同步锁，所以是非线程安全的。

- ⭐️:在Java中，同步锁是一种用于控制多个线程对共享资源访问的机制。它可以确保在同一时刻只有一个线程可以访问共享资源，从而避免了多个线程同时修改数据可能引发的数据不一致或不确定性问题。在Java中，每个对象都有一个内置的锁（也称为监视器锁或互斥锁），当线程进入被 synchronized 关键字修饰的代码块时，它会尝试获取对象的锁。如果该锁已被其他线程持有，那么线程将被阻塞，直到获取到锁为止。这样就确保了在同一时刻只有一个线程可以执行被同步的代码块，从而保证了线程安全性。

### ❓String s1 = new String("abc"),这段代码创建了几个字符串对象
- 会创建 1 或 2 个字符串对象。
    - 如果`字符串常量池`中不存在字符串对象“abc”的引用，那么它会在堆上创建两个字符串对象，其中一个字符串对象的引用会被保存在字符串常量池中。


