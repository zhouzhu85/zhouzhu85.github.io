---
layout: _posts
title: MyBatis面试题
date: 2023-12-11 21:28:39
tags:
  - 面试题
  - MyBatis
category: 
  - Java面试题
  - MyBatis
---
## MyBatis执行流程
读取MyBatis配置文件：mybatis-config.xml加载运行环境和映射文件，构造会话工厂SqlSessionFactory，会话工厂创建SqlSession对象（包含了执行SQL语句的所有方法），操作数据库的接口，Executor执行器，同时负责查询缓存的维护，Executor接口的执行方法中有一个MappedStatement类型的参数，封装了映射信息，其中是输入参数映射和输出结果映射。

## Mybatis是否支持延迟加载？
延时加载的意思是在需要用到数据时才进行加载，不需要用到数据时就不加载数据。MyBatis支持一对一关联对象和一对多关联集合对象的延迟加载，在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnable=ture|false,默认是关闭的

## 延迟加载的底层原理知道吗
Mybatis延迟加载底层是使用了CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器invoke方法，发现目标方法是null值，执行sql查询，获取数据以后，调用set方法设置属性值，再继续查询目标方法，就有值了。
