---
layout: _post
title: redis基础
date: 2023-12-18 21:44:43
tags:
---
## Redis数据结构
- 基本类型：String、Hash、List、Set、SortedSet
- 特殊类型：GEO、BitMap、HyperLog

## redis通用命令
通用命令是部分数据类型的，都可以使用的指令，常见的有：
- KEYS：查看符合模版的所有key，**注意，这命令不建议在生产环境设备上使用**
- DEL：删除一个指定的key
- EXISTS：判断key是否存在
- EXPIRE：给一个key设置有效期，有效期到期时该key会被自动删除
- TTL：查看一个key的剩余有效期

通过help [command] 查看一个命令的具体用法，例如：
![img.png](../images/redis1.png)