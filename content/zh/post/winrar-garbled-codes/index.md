---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "压缩包乱码解决方案"
subtitle: ""
summary: "解决压缩包乱码问题"
authors: []
tags: ["技术", "Windows"]
categories: ["技术"]
date: 2022-04-25T21:00:26+08:00
lastmod: 2022-04-25T21:00:26+08:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
由于Windows中文版默认采用GBK编码方式，打开utf-8编码的压缩包会出现文字乱码问题，而英文版系统打开GBK编码的压缩包也会出现乱码问题，因此需要对编码进行转换，从而显示正常的文字。

1. 首先下载[Winrar](https://www.winrar.com.cn/index.htm)
![20220425210635](https://vip1.loli.io/2022/04/25/4XVnxpBoGOh6TZm.png)

2. 安装后打开显示乱码的压缩包，在**选项**➡️**文件编码**处选择合适的编码（GBK-936或者Utf-8)，即可解决乱码问题。
![20220425211537](https://vip2.loli.io/2022/04/25/dmSMy7TaYfk5bOZ.png)
