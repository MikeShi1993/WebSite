---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "CMake and Visual Studio Tips"
subtitle: ""
summary: "Some tips about working with CMake and Visual Studio smoothly."
authors: []
tags: ['CMake', 'Visual Studio']
categories: ['CMake', 'C++']
date: 2020-01-15T17:21:54-05:00
lastmod:
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

See this [link](https://github.com/microsoft/vscode-cmake-tools/issues/1298#issuecomment-641959584) for reference.

Another way is:

`Settings: Cmake: Set Build Type On Multi Config`

- [x] Set CMAKE_BUILD_TYPE also on multi-config generators

### How to embed MSVC runtime in the executable file

``` bash
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
```

See [MSVC_RUNTIME_LIBRARY](https://cmake.org/cmake/help/latest/prop_tgt/MSVC_RUNTIME_LIBRARY.html#prop_tgt:MSVC_RUNTIME_LIBRARY) and [CMAKE_MSVC_RUNTIME_LIBRARY](https://cmake.org/cmake/help/latest/variable/CMAKE_MSVC_RUNTIME_LIBRARY.html#variable:CMAKE_MSVC_RUNTIME_LIBRARY) for reference.
