---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Colored Output in Terminal"
subtitle: ""
summary: "Change the color of text in terminal"
authors: []
tags: []
categories: ["C++"]
date: 2020-03-02T22:43:20-05:00
lastmod: 2020-03-02T22:43:20-05:00
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
Here is the terminal codes for changing the color of the text in terminal. This C++ practice is from a [Stack overflow answer](https://stackoverflow.com/questions/9158150/colored-output-in-c/9158263).

``` C++
//the following are UBUNTU/LINUX, and MacOS ONLY terminal color codes.
#pragma once
#include <string_view>
constexpr std::string_view RESET = "\033[0m";
constexpr std::string_view BLACK = "\033[30m";                 /* Black */
constexpr std::string_view RED = "\033[31m";                   /* Red */
constexpr std::string_view GREEN = "\033[32m";                 /* Green */
constexpr std::string_view YELLOW = "\033[33m";                /* Yellow */
constexpr std::string_view BLUE = "\033[34m";                  /* Blue */
constexpr std::string_view MAGENTA = "\033[35m";               /* Magenta */
constexpr std::string_view CYAN = "\033[36m";                  /* Cyan */
constexpr std::string_view WHITE = "\033[37m";                 /* White */
constexpr std::string_view BOLDBLACK = "\033[1m\033[30m";      /* Bold Black */
constexpr std::string_view BOLDRED = "\033[1m\033[31m";        /* Bold Red */
constexpr std::string_view BOLDGREEN = "\033[1m\033[32m";      /* Bold Green */
constexpr std::string_view BOLDYELLOW = "\033[1m\033[33m";     /* Bold Yellow */
constexpr std::string_view BOLDBLUE = "\033[1m\033[34m";       /* Bold Blue */
constexpr std::string_view BOLDMAGENTA = "\033[1m\033[35m";    /* Bold Magenta */
constexpr std::string_view BOLDCYAN = "\033[1m\033[36m";       /* Bold Cyan */
constexpr std::string_view BOLDWHITE = "\033[1m\033[37m";      /* Bold White */
```
