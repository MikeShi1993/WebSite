---
title: Python字典操作中注意事项
summary: Python编程在字典操作中遇到的一个坑
date: "2014-09-09T21:01:29Z"
tags: ["Python", "技术"]
categories: ["Python"]
reading_time: true  # Show estimated reading time?
share: false  # Show social sharing links?
profile: true  # Show author profile?
comments: false  # Show comments?
---

我在进行字典操作的时候，碰到了Python中一个不算是坑的坑，让我找bug找了一个多小时，逻辑错误果然伤不起。。。在Python中dict.fromkeys(seq,val=None)的命令为创建并返回一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值(默认为None)。**但是注意在设置val=[]是，采取的是引用，而不是为每个键产生一个独立的列表，在采取列表操作的时候可能会出错，所以在使用这个内置函数的时候要避免此类错误。例子如下：

```bash
>>> a={}.fromkeys([1,2,3],[])
>>> a
{1: [], 2: [], 3: []}
>>> a[1].append("b")#可能产生一个引用的逻辑错误
>>> a
{1: ['b'], 2: ['b'], 3: ['b']}
```
