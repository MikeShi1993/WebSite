---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Installation of zsh and beautify"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-01-19T19:50:06-05:00
lastmod: 2020-01-19T19:50:06-05:00
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

The [Zsh](https://en.wikipedia.org/wiki/Z_shell) is a [Unix shell](https://en.wikipedia.org/wiki/Unix_shell), which has been developed since 1990. Especially by the extensions you can install via the [Oh My Zsh](http://ohmyz.sh/) framework, the work in the termial is greatly simplified.

1. Install zsh by running

```bash
sudo apt-get install zsh
```

2. Verify installation by running `zsh --version`. Expected result: zsh 5.1.1 or more recent.

3. Make it your default shell: `chsh -s $(which zsh)`

4. Install [Oh My Zsh](http://ohmyz.sh/) via wget
```bash
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

5. Change Zsh theme to agnoster. Set `ZSH_THEME` to the name of the theme in your ~/.zshrc, before sourcing Oh My Zsh; for example: `ZSH_THEME=agnoster`

6. Install one of the [patched fonts from Vim-Powerline](https://github.com/powerline/fonts) for the special characters.

7. Install [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md) to zsh.

   If meet on my zsh safty issues `chmod 755 ${plugin-directory}`

8. Install [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md)