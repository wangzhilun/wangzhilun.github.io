---
title: hashmap hash方法
date: 2019-09-28 14:06:01
categories:
 - data structure
 - hashmap
tags:
 - java
 - data structure
 - hashmap
---

## hashmap hash方法
我们可以看到,hashmap的hash方法是:
```java
    static final int hash(Object key) {
        int h;
        return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
    }
```
图中可以看出,hashmap是允许key 为null的。

我们知道,平时hashcode()都是32位,我们看到最后的hash值是hash值的低位与高位做了异或运算。为什么要做额外的处理呢,我们查看下定位值的方法,发现只有hash值的低四位参加了运算,设计者考虑到现在的hashCode分布的已经很不错了，而且当发生较大碰撞时也用树形存储降低了冲突。仅仅异或一下，既减少了系统的开销，也不会造成的因为高位没有参与下标的计算(table长度比较小时)，从而引起的碰撞。



附录：
- [位运算](https://laoshirenclub.com/2019/09/28/bitoperation/)
- [hashmap源码分析](https://laoshirenclub.com/categories/java/hashmap/)

