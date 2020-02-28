---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Boost Graph Library(BGL)"
subtitle: "Graphs are mathematical abstractions that are useful for solving many types of problems in computer science."
summary: ""
authors: []
tags: []
categories: []
date: 2019-10-22T09:55:32-04:00
lastmod: 2019-10-22T09:55:32-04:00
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

### Create an undirected boost graph using BGL

``` C++
typedef adjacency_list<boost::vecS, boost::vecS, boost::undirectedS> Graph;
typedef graph_traits<Graph>::vertex_descriptor Vertex;
typedef graph_traits<Graph>::vertex_iterator Vertex_iterator;
property_map<Graph, vertex_name_t>::type bin_ptr = boost::get(vertex_name, g_bin);
auto iter = empty_bins.begin();
for (auto vp = boost::vertices(g_bin); vp.first != vp.second; ++vp.first, ++iter) {
    bin_ptr[*vp.first] = *iter;
}
```
