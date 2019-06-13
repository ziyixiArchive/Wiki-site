---
title: SeisScript
toc: true
date: 2019-06-11 17:07:03
tags: FWI
categories: FWI
---

## Overview

Recently I have collected some of my research scripts into a package (or just a directory) named [SeisScript](https://github.com/ziyixi/SeisScripts). This package is very useful for the need of full waveform inversion in the study of seismology. Here I'd like to introduce different parts.

## specfem_helper.jl

At the moment, this package contains two different usable programs. (and more usable functions!) They are all inside the src/program subdirectory. Before using them, we may have to enter the `fortran` directory to run `julia compile.jl` to compile two fortran files into the dynamic library so that we can use `ccall` to call them. (I can write them in pure Julia, but I'm pretty lazy.) Also we have to edit `setting/constants.jl` to edit `ANGULAR_WIDTH_XI_IN_DEGREES_VAL`, `ANGULAR_WIDTH_ETA_IN_DEGREES_VAL`, `NEX_XI_VAL` and `NEX_ETA_VAL`.

The first program is named as `xsem_interp_mesh2.jl`, direcctly adapted from [Tao Kai's code](https://github.com/taotaokai/sem_utils/blob/master/src/program/xsem_interp_mesh2.f90). But I have used some packages directly from Julia which makes the code more neat and more beautiful. According to my test, this program will have the same result with Tao's code, but three time slower. (That's reasonable, since Julia seems to be slower than Fortran, but I'm planning to precompile some parts to make it faster.)

The second program is named as `get_cross_section_data.jl`. This program is mainly used to calculated the point values along a specific profile of the GLL model. Previously we have a [script](https://github.com/geokid/specfem3D_visualization/tree/master/create_slice_xyz) which is designed to find the nearest points along the interface of the profile. This method is somehow not accurate. So I'm using the interpolation to calculate the values. Comparing with the previous code, this program runs faster and uses less computing resources.
