---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Enable Proxy in WSL2"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2021-10-06T23:28:41+08:00
lastmod: 2021-10-06T23:28:41+08:00
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

1. Check the ip address of windows in the local network.
2. Update proxy in the linux
``` bash
export all_proxy="socks5://192.168.0.104:7890"
```
3. Check if the proxy works
``` bash
curl cip.cc
```