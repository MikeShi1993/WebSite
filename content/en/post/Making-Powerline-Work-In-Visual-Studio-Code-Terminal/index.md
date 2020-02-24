---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Making Powerline Work in Visual Studio Code Terminal"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-02-23T16:55:32-05:00
lastmod: 2020-02-23T16:55:32-05:00
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

The integrated terminal of VScode will show garbled words if zsh is installed but PowerLine font is not set. In order to fix this problem:

1. One of the [patched fonts from Vim-Powerline](https://github.com/powerline/fonts) for the special characters. (if you don't have any one.)

2. In your User Settings (Code | Preferences | Settings) add this:

  ``` json
  {
  "terminal.integrated.fontFamily": "Hack",
  }
  ```
