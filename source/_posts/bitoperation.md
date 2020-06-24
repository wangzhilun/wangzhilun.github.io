---
title: 位运算
date: 2019-09-28 10:06:01
categories: 
   - java
tags: 
   - java
   - algorithm
---

## java位运算

### 异或运算
`^` ,二进制运算,相同为0,不同为1

hashmap计算hash时,有一个异或运算,为了方便把hash变的均匀。
```java
static final int hash(Object key) {
        int h;
        return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
    }
```

### 与运算
`&`,二进制计算,只要有一个为0,就为0
常做取余算法。 
```java
System.out.println((129/128) ==(129 & 127));
```
### 或方法
`|` 二进制计算,两个数只要有一个为1则为1，否则就为0

### 非方法
`~`

### << 向左位移
针对二进制，转换成二进制后向左移动n位，后面用0补齐
### >>(向右位移)
针对二进制，转换成二进制后向右移动n位，
### >>>(无符号右移)  
无符号右移，忽略符号位，空位都以0补齐
hash值右移获取高位
```java
static final int hash(Object key) {
        int h;
        return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
    }
```

