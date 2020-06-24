---
title: hashmap 如何把大小设置为2的幂次方
date: 2019-09-28 17:26:01
categories:
- data structure
- hashmap
tags:
- hashmap
- algorithm
---

## hashmap 如何把大小设置为2的幂次方

我们看hashmap源码发现有一个方法,
```
    static final int tableSizeFor(int cap) {
        int n = cap - 1;
        n |= n >>> 1;
        n |= n >>> 2;
        n |= n >>> 4;
        n |= n >>> 8;
        n |= n >>> 16;
        return (n < 0) ? 1 : (n >= MAXIMUM_CAPACITY) ? MAXIMUM_CAPACITY : n + 1;
    }
```
用于把bucket的大小设置为2的幂次方。
先来分析有关n位操作部分：先来假设n的二进制为01xxx...xxx。接着

对n右移1位：001xx...xxx，再位或：011xx...xxx

对n右移2为：00011...xxx，再位或：01111...xxx

此时前面已经有四个1了，再右移4位且位或可得8个1

同理，有8个1，右移8位肯定会让后八位也为1。

综上可得，该算法让最高位的1后面的位全变为1。

最后再让结果n+1，即得到了2的整数次幂的值了。

因为int最大为32位,那么位移31位就可以了。这样从第一位开始所有位数都是1.