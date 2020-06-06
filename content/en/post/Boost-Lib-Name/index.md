---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Don't let boost mangle your lib name"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-06-06T00:16:16-04:00
lastmod: 2020-06-06T00:16:16-04:00
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
If you use conan to manage Boost libraries, the default boost lib name is `libboostxxxx.lib`. However, boost system links the lib with tags sometimes. It may cause the linker cannot find libs properly. So it may be necessary to specify the pre-definition to avoid boost mangling the names. 


`BOOST_AUTO_LINK_NOMANGLE`: Specifies that we should link to BOOST_LIB_NAME.lib,
                          rather than a mangled-name version.

`BOOST_AUTO_LINK_TAGGED`:   Specifies that we link to libraries built with the --layout=tagged option.
                          This is essentially the same as the default name-mangled version, but without
                          the compiler name and version, or the Boost version.  Just the build options.

`BOOST_AUTO_LINK_SYSTEM`:   Specifies that we link to libraries built with the --layout=system option.
                          This is essentially the same as the non-name-mangled version, but with
                          the prefix to differentiate static and dll builds