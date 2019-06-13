---
title: Comparision of different filters in preprocessing data
toc: true
date: 2019-06-11 17:07:03
tags: filter
categories: DSP
---

## Filters

In the seismic research, we have to preprocess the data. Specially in the field of FWI, we may have to compare the synthetics and the data, and then calculate the misfit function. Here I compare two different way to get our desired frequency range.

### Bandpass

The data we have the [data](https://wiki.ziyixi.science/static/data/AH.DYN.BHZ.trim) and the [PZ file](https://wiki.ziyixi.science/static/data/AH.DYN.BHZ.pz). And then we can use SAC to preprocess it:

```bash
r AH.DYN.BHZ.trim
rmean; rtr; taper;
trans from polezero s ./AH.DYN.BHZ.pz to none freq 0.004 0.005 1 1.2
bp n 2 p 2 c 0.01 0.0025
```

So here we will get the processed data with the frequency range of 40s to 100s.

### Taper in the frequency domain

We can also directly get the final result as:

```bash
r AH.DYN.BHZ.trim
rmean; rtr; taper;
trans from polezero s ./AH.DYN.BHZ.pz to none freq 0.008 0.01 0.0025 0.03
```

## Result

We can compare the result as:
![](https://wiki.ziyixi.science/static/figures/compare.png)

As we can see, the black line represents "taper from 0.004HZ to 0.005HZ" and then removing the instrumental response, while the blue line represents "taper from 0.01HZ to 0.0025HZ" and then removing the instrumental response. And the red line represnets apply a bandpass filter from 0.01HZ to 0.0025HZ to the black line.

In FWI research, we want to keep as much as energy in our desired frequency band. So it seems the blue has not losed the energy, which is better then the red line. Also the blue line has almost the same amount of enery with the red line. However, there is an abrupt jump of the blue line, which may cause some artifact.

![](https://wiki.ziyixi.science/static/figures/waveform_compare.png)

Look at part from 800s to 1000s. It seems the "phases" in the black line are the artifact, which may cause some problem for the comparision of the surface wave. Anyway, the behavior of sync and data outside our desired frequency range is somehow different.
