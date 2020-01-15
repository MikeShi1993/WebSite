---
title: "CMAKE"
subtitle: ""
summary: "CMake is tool for automatically compiling C++ programs."
authors: []
tags: []
categories: []
date: 2019-09-23T21:32:18-04:00
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
```bash
cmake_minimum_required(VERSION 3.14)
project(MPI_Learn)

set(CMAKE_CXX_STANDARD 17)
find_package(MPI REQUIRED)
if (MPI_FOUND)
    include_directories(SYSTEM ${MPI_INCLUDE_PATH})
else (MPI_FOUND)
    message(SEND_ERROR "This application cannot compile without MPI")
endif (MPI_FOUND)
SET(CMAKE_CXX_COMPILER ${MPI_CXX_COMPILER})
add_executable(MPI_Learn main.cpp)
#MESSAGE (STATUS "MPI_CXX_COMPILER ${MPI_CXX_COMPILER}")
```
