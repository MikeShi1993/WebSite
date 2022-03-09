---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Synology public network access settings"
subtitle: ""
summary: "This post discusses how to set the public network access for Synology NAS."
authors: []
tags: ["Synology"]
categories: ["Network"]
date: 2022-03-09T18:53:47+08:00
lastmod: 2022-03-09T18:53:47+08:00
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
### Improve the security of NAS

1. Do not allow DSM to be embedded with iFrame.
![20220309193203](https://vip2.loli.io/2022/03/09/MyFkbWUXqShVxpE.png)

2. Enable firewall and edit rules
![20220309193528](https://vip1.loli.io/2022/03/09/2vYnTADN4drBXhq.png)

3. Turn on auto block
![20220309193924](https://vip1.loli.io/2022/03/09/5ocA8ixbMwE6qyj.png)

4. Turn on account 2-Factor Authentication and Account Protection
![20220309194032](https://vip2.loli.io/2022/03/09/dv84BU2NkYzKIcp.png)

### VPN server settings

Turn on Openvpn server and export configuration
![20220309194354](https://vip1.loli.io/2022/03/09/NplLvuWEeO1F2Cf.png)

### DDNS settings

Add ddns record for the NAS and adjust home router settings (not NAS).
