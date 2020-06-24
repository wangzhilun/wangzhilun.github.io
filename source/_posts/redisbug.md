---
title: redis bug
date: 2019-07-04 10:46:01
categories: 
   - bug
tags: 
   - bug
   - redis
---

使用springboot redis,配置没有问题,但是一直报错netty.UnResolveAddressException。经过排查发现,springboot redis 需要引用netty 4.1.x 的包,项目中有4.0.x的netty依赖。排除掉依赖恢复正常。