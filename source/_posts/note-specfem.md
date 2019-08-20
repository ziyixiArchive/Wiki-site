---
title: Some notes on Specfem3D
toc: true
date: 2019-07-22 10:41:23
tags: specfem
categories: specfem
---

## Some bugs I find

1. The newer version(7.0.2) hasn't enabled USE_FULL_TISO_MANTLE by default. We should turn it on.

2. Find a bug in Specfem3D-globe(v7.0.0) about writing to the ASDF format. In write_specfem_adios_header.F90, line 53, we should remove “NSOURCES” as this object has been declared by the module shared_parameters in line 48.

3. Find a bug in Specfem3D-globe(v7.0.0). We should change Adios_manager.f90:line58: adios_allocate_buffer (ADIOS_BUFFER_SIZE_IN_MB, adios_err) to adios_set_max_buffer_size(ADIOS_BUFFER_SIZE_IN_MB)

## Bugs fixed by the newer version

1. [seismograms in RTZ system](https://github.com/geodynamics/specfem3d_globe/issues/424)

## Interesting commit

1. [A GMT script to plot cross section](https://github.com/geodynamics/specfem3d_globe/commit/3f0596bfb1a643b1a78b3bb999a91720922b5d00)

2. [The flag to set the tiso range](https://github.com/geodynamics/specfem3d_globe/commit/f0ccd5d880c6ea7a0a86dd20899769309b9148c4)

3. [Directly set Crust in the Parfile](https://github.com/geodynamics/specfem3d_globe/commit/1bdd5b6e7d7a3be59a95afe898c58804868b99bf)

