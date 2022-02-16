---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Tips for Clash-For-Windows"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2022-02-17T00:46:24+08:00
lastmod: 2022-02-17T00:46:24+08:00
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

### Clash For Windows Profile Preprocessing

In order to force chinese version OneDrive connecting through domestic ip, you need to preprocess the configuration file with the download link and do the following:

1. Go to the Settings interface
2. Scroll to the Profiles bar
3. Click Parsers to the right of Edit to open the editor, filling the following code

``` yaml
parsers: # array
  - url: https://api.immtel.co/Subscription/Clash?sid=1329&token=vGxuZs4HAG0
    yaml:
      prepend-rules:
        - DOMAIN-SUFFIX,partner.microsoftonline.cn,China-Websites
        - DOMAIN,microsoftgraph.chinacloudapi.cn,China-Websites
```

### Solve internet connection error for Microsoft apps

Simply turn on the following option:

``` bash
General➡️UWP Loopback➡️Exempt all
```

### Solve pip download ssl errors

Simply turn on the following option:

``` bash
Settings➡️System Proxy➡️Specify Protocol
```
