---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Compiling LAMMPS"
subtitle: ""
summary: ""
authors: []
tags: ['LAMMPS']
categories: ['LAMMPS']
date: 2020-02-23T17:04:40-05:00
lastmod: 2021-10-26T17:04:40-05:00
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
1. Download [LAMMPS](http://lammps.sandia.gov/download.html)

2. Download [Zlib](https://www.zlib.net/)

3. Install [Zlib](https://www.zlib.net/)

  ``` bash
  make distclean
  ./configure
  make
  make install
  ```

4. Install dependencies like [BLAS](http://www.netlib.org/blas/), [LAPACK](http://www.netlib.org/lapack/), [GSL](https://www.gnu.org/software/gsl/) and [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page). For Manjaro users, you could install these libraries by the `pacman` command:

``` bash
sudo pacman -Syu blas lapack gsl eigen
```

5. Create a software folder in your home directory (ie. ‘mkdir ~/soft’)

6. Untar the lammps tarball (ie. ‘tar -xvf lammps-stable.tar.gz’)

7. Go to the lammps src folder (ie. ‘cd lammps-*/src’)

8. Compile lammps (ie. make mpi)

``` bash
cmake -C ../cmake/presets/most.cmake   -D PKG_MANYBODY=yes  -D PKG_RIGID=yes -D PKG_MISC=yes -D PKG_USER-REAXC=yes -D PKG_MOLECULE=yes -D PKG_USER-DIFFRACTION=yes -D PKG_GPU=yes -D GPU_API=cuda -D GPU_ARCH=sm_75 -D CUDA_MPS_SUPPORT=yes -D PKG_COMPRESS=yes -D ZLIB_INCLUDE_DIR=/usr/local/include -D ZLIB_LIBRARIES=/usr/local/lib ../cmake  # configuration with (command-line) cmake
```

-------------------------------------------------
Zhengzhou University Supercomputer installation guide

``` bash
module load compiler/cmake/3.15.6 mathlib/fftw/3.3.8/double/gnu
cmake -C ../cmake/presets/most.cmake -D FFT=fftw3 -D FFTW3_LIBRARY=/public/software/mathlib/fftw/3.3.8/double/gnu/lib/libfftw3.a -D CMAKE_Fortran_COMPILER=gfortran -D BUILD_MPI=yes -D PKG_KIM=yes -D DOWNLOAD_KIM=no   ../cmake
```
