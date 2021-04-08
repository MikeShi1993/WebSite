---
title: "CMAKE"
subtitle: ""
summary: "CMake is tool for automatically compiling C++ programs"
authors: []
tags: ["C++", "CMake"]
categories: ["C++", "Coding"]
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
``` CMake
cmake_minimum_required(VERSION 3.19)
project(chapter1 VERSION 0.11 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_BINARY_DIR})
list(APPEND CMAKE_PREFIX_PATH ${CMAKE_BINARY_DIR})

if(NOT EXISTS "${CMAKE_BINARY_DIR}/conan.cmake")
  message(STATUS "Downloading conan.cmake from https://github.com/conan-io/cmake-conan")
  file(DOWNLOAD "https://raw.githubusercontent.com/conan-io/cmake-conan/v0.16.1/conan.cmake"
                "${CMAKE_BINARY_DIR}/conan.cmake"
                TLS_VERIFY ON)
endif()

include(${CMAKE_BINARY_DIR}/conan.cmake)

conan_cmake_configure(REQUIRES fmt/7.1.3
                      GENERATORS cmake_find_package
                      OPTIONS fmt:shared=False
                      OPTIONS fmt:header_only=True)

string(TOUPPER ${CMAKE_BUILD_TYPE} COMPILE_BUILD_TYPE)
if (${COMPILE_BUILD_TYPE} STREQUAL "DEBUG")
    SET(msvc_link_setting compiler.runtime=MTd)
else()
    SET(msvc_link_setting compiler.runtime=MT)
endif()

conan_cmake_autodetect(settings)
conan_cmake_install(PATH_OR_REFERENCE .
                    BUILD missing
                    REMOTE conan-center
                    SETTINGS ${settings}
                    SETTINGS ${msvc_link_setting})

find_package(fmt)

# Embed msvc runtime library in the executable file
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

add_library(airline_ticket airline_ticket.cppm airline_ticket.cpp)
set_target_properties(airline_ticket PROPERTIES LINKER_LANGUAGE Cxx) 

add_executable(${PROJECT_NAME} chapter1.cpp  employee.cppm airline_ticket.cppm)
target_link_libraries(${PROJECT_NAME} PRIVATE fmt::fmt-header-only airline_ticket)  

if (CMAKE_CXX_COMPILER_ID STREQUAL "MSVC")
    target_compile_options(${PROJECT_NAME} PRIVATE "/experimental:module" "/std:c++latest" "/W4" "/translateInclude")
    get_target_property(TARGET_SOURCES "${PROJECT_NAME}" SOURCES)
    set_property(TARGET ${PROJECT_NAME} PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    set_source_files_properties(${TARGET_SOURCES} PROPERTIES VS_TOOL_OVERRIDE "ClCompile")

elseif (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    message(WARNING "GNU")
    target_compile_options(${PROJECT_NAME} PRIVATE "-std=c++2a")
endif()
```
