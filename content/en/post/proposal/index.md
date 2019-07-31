---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Study of high-temperature diffusion of gas in low density amorphous carbon(Char) by Molecular Dynamics"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2019-07-31T10:30:10-04:00
lastmod: 2019-07-31T10:30:10-04:00
featured: false
draft: true

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

## Mesoporous VS. Microporous

A **microporous** material is a material containing pores with diameters less than 2 nm.

A **mesoporous** material is a material containing pores with diameters between 2 nm and 50nm.

In general, diffusion is expected to increase with decreasing concentration due to smaller scattering frequency and longer mean free paths.

## Pyrolysis

The thermochemical decomposition of organic materials at elevated temperatures in the absence of oxygen.

#### What are the key scientific questions?

How pyrolysis gas diffuse in different amorphous carbon structure? How the density of amorphous carbon influence the diffusivity of pyrolysis gas? How the composition of pyrolysis gas influence the diffusivity in the char?

#### What is the gap in understanding that the prior studies did not address?

Ranganathan has investigated H<sub>2</sub>, O<sub>2</sub>, CO, H<sub>2</sub>O diffusivity in microporous and mesoporous amorphous carbon. However, pyrolysis gas is the mixture of several different molecules like  C<sub>2</sub>H<sub>2</sub>, C<sub>6</sub>H<sub>6</sub>, O<sub>2</sub>, H<sub>2</sub>. Therefore, we need to study the diffusivity of these large molecules in amorphous carbon and the mixed gas diffusivity in the porous carbon.

How can the methods you suggest address those questions?
Liquid quench method will be used to create different densities' amorphous carbon structure. LAMMPS and reaxff potential will be used in the simulation. Zeo++ will be used to calculate the pore size and accessible pore volume size. Ring code will be used to investigate the number of rings in the structure. Both velocity correlation function and mean squared method will be used to calculate diffusion coefficient.
What do you expect to learn?
The diffusivity of large molecules in the different densities' amorphous carbon and the influence of pure single molecule gas and mixture gas on diffusivity in the different densities' amorphous carbon.
Initial stage of phenolic resin pyrolysis simulation by DFT(Ab-initio MD) and molecular dynamics
Motivation
The pyrolysis reactions convert the phenolic matrix to amorphous carbon. In order to keep stresses below the critical level that would cause damage to the part, the rate of gas production is controlled by controlling the heating rate of the composite. Because the pyrolysis reactions are not well understood, a large factor of safety must be used when determining heating rates. This leads to excessively long cycle times. Also the limited understanding of the reactions requires that process cycles be developed by trial and error methods. Long cycle times and trial and error process cycle development leads to high processing costs. An increased understanding of the pyrolysis reactions is essential for improvement of the processing of carbon/carbon. 
Trick, Kimberly A., and Tony E. Saliba. "Mechanisms of the pyrolysis of phenolic resin in a carbon/phenolic composite." Carbon 33.11 (1995): 1509-1515.