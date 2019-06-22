---
title: lasif_specfem
toc: true
date: 2019-06-14 10:46:24
tags: FWI
categories: FWI
---

## Overview

I'm planning to build a package named LASIF_Specfem. This package aims to create a command line tool to manage the usage of Specfem-globe. As we know that Specfem is kind of complex, and rewrite it to the structure of what a modern software should look like is difficult and complex. But anyway, we can write a python interface to it. According to [LASIF_2.0](https://github.com/dirkphilip/LASIF_2.0), we can use directory structures to manage our data, synthetics and more. 

There have already been some tools, but the problem is that these tools have some default setting which instructs you each steps. Since the scientific research is really flexble, such a restriction is not tolerable. So I'm planning to use "plugins" to solve this problem. The package LASIF_Specfem will only contain prototypes and set up the directory structure, and users can implement their own plugins following some interfaces.