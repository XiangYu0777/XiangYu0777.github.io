---
title: Redis Snippet
layout: post
tags: Redis 数据库
---

### 基本数据类型

 字符串 string、列表 list、无序集合 set、有序集合 zset、散列表 hash。
 
### 支持的特性
* 将内存中的数据持久化到硬盘
* 使用**复制**来扩展**读性能**
* 使用**分片**来扩展**写性能**

### 键的过期时间
对于散列表这种容器，只能为整个键设置过期时间（整个散列表），而不能为键里面的单个元素设置过期时间。