---
title: springcloud 注册中心
date: 2019-07-01 10:06:01
categories: 
   - springcloud源码分析
tags: 
   - springcloud
   - eureka
---
首先我们看下Netflix官方给的图
![图](https://raw.githubusercontent.com/wangzhilun/wangzhilun.github.io/master/image/netflix.jpg)

##  注册中心eureka
开启eureka服务端很简单,只需要在添加注解`@EnableEurekaServer`即可。一般来说添加一个注解开启一个功能,主要是通过import导入一个configuration.我们可以看到`@EnableEurekaServer`注解其实是引入了`EurekaServerConfiguration`配置。我们看下里面配置了哪些内容。

首先我们看到,里面配置了`EurekaServerConfigBeanConfiguration`,这个类会配置一个一份`EurekaServiceConfig`,里面包含了所有配置的enruka server属性。
配置了一个eureka的看板,通过看板我们能看到有多少个服务接入了server. 
配置了一些eureka nodes，用来做高可用集群使用。  
配置了注册中心,我们主要来看下这个注册中心. 

## 注册中心 `PeerAwareInstanceRegistryImpl`

### 注册 
`register()`
### 注销
`cancle()`
### 续约
`renew()`
### 定时清理
`evic()`

## 集群
`PeerEurekaNodes` 包含了集群其他节点的信息
`replicateToPeers`.将应用状态更新到其他节点

## 注册接口
`ApplicationResource`
