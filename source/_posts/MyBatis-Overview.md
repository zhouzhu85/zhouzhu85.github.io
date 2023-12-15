---
layout: _posts
title: MyBatis
date: 2023-12-11 21:28:39
tags:
  - MyBatis
category: 
  - Java
  - MyBatis
---
## MyBatis执行流程
读取MyBatis配置文件：mybatis-config.xml加载运行环境和映射文件，构造会话工厂SqlSessionFactory，会话工厂创建SqlSession对象（包含了执行SQL语句的所有方法），操作数据库的接口，Executor执行器，同时负责查询缓存的维护，Executor接口的执行方法中有一个MappedStatement类型的参数，封装了映射信息，其中是输入参数映射和输出结果映射。

## Mybatis是否支持延迟加载？
延时加载的意思是在需要用到数据时才进行加载，不需要用到数据时就不加载数据。MyBatis支持一对一关联对象和一对多关联集合对象的延迟加载，在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnable=ture|false,默认是关闭的

## 延迟加载的底层原理知道吗
Mybatis延迟加载底层是使用了CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器invoke方法，发现目标方法是null值，执行sql查询，获取数据以后，调用set方法设置属性值，再继续查询目标方法，就有值了。

## Mybatis的一级、二级缓存用过吗？
- 一级缓存：基于PerpetualCache的HashMap本地缓存，其存储作用域为Session，当Session进行flush或close之后，该Session中的所有Cache就将清空，默认打开一级缓存
- 二级缓存：基于namespace和mapper的作用域起作用的，不是依赖于SQL Session，默认也是采用PerpetualCache，HashMap存储，需要单独开启，一个是核心全局配置（cacheEnable设置为true），一个是mappper映射文件，加入<cache/>标签

## Mybatis的二级缓存什么时候会清理缓存中的数据
当某一个作用域（一级缓存Session或二级缓存Namespaces）的进行了新增、修改、删除操作后，默认该作用域下所有select中的缓存将被清除。    