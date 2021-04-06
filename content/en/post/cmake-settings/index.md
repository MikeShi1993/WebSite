---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "CMake and Visual Studio Tips"
subtitle: ""
summary: ""
authors: []
tags: ['CMake', 'Visual Studio']
categories: ['CMake', 'C++']
date: 2020-01-15T17:21:54-05:00
lastmod: 2020-01-15T17:21:54-05:00
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

### How to change working directory in Visual Studio

Select **Debug** or **Debug and Launch Settings** then add

``` bash
"currentDir": "${ProjectDir}"
```

### How to enable CMake multi-config in Visual Studio Code

CMake supports two types of generators: single-configurations (makefiles, nmake) and multi-configurations (IDEs). By adding the following lines to ```settings.json```. This should then update your ```CMAKE_BUILD_TYPE``` accordingly and set it as -D CLI option.

``` bash
"cmake.configureSettings": {
   "CMAKE_BUILD_TYPE": "${buildType}"
}
```

see this [link](https://github.com/microsoft/vscode-cmake-tools/issues/1298#issuecomment-641959584) for reference.
