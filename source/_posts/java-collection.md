---
layout: _post
title: Java集合
date: 2023-11-30 10:22:50
tags: 
  - 集合
category: 
  - Java
  - 集合
---
## HashMap和Hashtable的区别
**线程是否安全**：HastMap是非线程安全的，Hashtable是线程安全的，因为Hashtable内部的方法基本都经过synchronized修饰（如果要保证线程安全的话就用ConcurrentHashMap）;

**效率**：因为线程安全的问题，HashMap要比Hashtable效率高一点。但Hashtable基本被淘汰了，就不要在代码中使用了

**对Null key 和Null value的支持**：HashMap允许键值都可以为null，但null的键只能只有一个，值可以多个null，Hashtable是不允许键值都是null，否则会报空指针异常

**初始容量大小和每次扩充容量大小的不同**：
1. 创建时如果不给定容量大小，Hashtable默认初始的容量大小为11，之后每次扩充，都是原来的2n+1。HashMap默认初始的容量大小为16，之后每次扩充，都是原来的2倍。
2. 创建时如果给定容量大小，Hashtable就直接使用给定容量，HashMap会将其扩充为2的幂次方大小

**底层数据结构**：JDK1.8以后HashMap在解决哈希冲突时有了较大的变化，当链表长度大于阈值时，阈值默认是8，就将链表转化为红黑树，但在转化成红黑树之前，HashMap会判断当前数组长度是否大于64，如果小于64，就会选择进行扩容，不转化成红黑树，要是超过64，就转化红黑树，
红黑树目的就是为了减少检索时间。Hashtable没有这样机制。

## HashMap 和 HashSet 区别
HashSet 底层就是基于 HashMap 实现的。（HashSet 的源码非常非常少，因为除了 clone()、writeObject()、readObject()是 HashSet 自己不得不实现之外，其他方法都是直接调用 HashMap 中的方法。

