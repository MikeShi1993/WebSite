---
title: 获取Python脚本所在目录的正确方法
summary: xlwt是Python一个编辑xls文件的模块，它生成的文件能很好的与Excel2000/2003/OpenOffice/Gnumeric兼容，并且完美支持unicode。通过xlwt模块Excel表格可以在任何平台生成，不需要依赖Excel或者COM服务器。
date: "2015-11-17T19:22:26Z"
tags: ["Python", "技术", "Linux"]
categories: ["Python"]
reading_time: true  # Show estimated reading time?
share: false  # Show social sharing links?
profile: true  # Show author profile?
comments: false  # Show comments?
---

### 以前的方法

如果是要获得程序运行的当前目录所在位置，那么可以使用os模块的`os.getcwd()`函数。

### 正确的方法

但以上这些其实都不是脚本文件所在目录的位置,获取Python脚本所在目录实际应使用`os.path.split(os.path.realpath(__file__))[0]`其中`__file__`虽然是所在.py文件的完整路径，但是这个变量有时候返回相对路径，有时候返回绝对路径，因此 还要用`os.path.realpath()`函数来处理一下。
