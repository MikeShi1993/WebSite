---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Linux Slurm"
subtitle: ""
summary: ""
authors: []
tags: ["Linux", "Slurm"]
categories: ["Linux"]
date: 2022-03-31T22:50:04+08:00
lastmod: 2022-03-31T22:50:04+08:00
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

### Screen command

``` bash
screen -S yourname # Create a new session called "yourname"
screen -ls         # list all current sessions
scree -r yourname  # return to the "yourname" session
screen -d yourname # detach "yourname" session
```

### Salloc command

```bash
salloc -p fat -N 1 -n 32 --gres=dcu:4 -t=168:00:00

# generate MPI needed machine file
srun hostname -s | sort -n > slurm.hosts
mpirun -np 32 -machinefile slurm.hosts hostname
```
