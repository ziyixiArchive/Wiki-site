---
title: Files in ICER and Stampede2
toc: true
date: 2019-07-16 10:17:46
tags: stampede2,icer
categories: hpcc
---

## Overview
Managing files in ICER and STAMPEDE2 is a important and I am supposed to find a way to place my files in order. That the reason why I write this wiki.

## The summary of the storage space
In ICER, we have these four "disks": (directly copied)
```sh
Home Directory:
---------------------------------------------------------------------------------------------------------------------

/mnt/home/xiziyi                Quota          Used           Free           Files Quota    Files Used     Files Free
                                1024G          251G           773G           1048576        988008         60568


Research Groups:                Space          Space          Space          Files          Files          Files
                                Quota          Used           Available      Quota          Used           Available
------------------------------------------------------------------------------------------------------------------
seismolab2                      16384G         10797G         5587G          26214400       24725040       1489360

Temporary Filesystems:
---------------------------------------------------------------------------------------------------------------------

/mnt/ls15 (legacy scratch)      Inodes Used     Quota           Free
                                115170          1000000         884830
/mnt/scratch (/mnt/gs18)        Space Quota    Space Used     Space Free     Filess Quota   Files Used     Files Free
                                51200G         340G           50860G         1048576        71699          976877
```

And in stampede2, we have:
```sh
--------------------- Project balances for user tg851791 ----------------------
| Name           Avail SUs     Expires | Name           Avail SUs     Expires |
| TG-EAR140030       31763  2019-09-30 | TG-EAR130011       87905  2019-09-30 |
------------------------ Disk quotas for user tg851791 ------------------------
| Disk         Usage (GB)     Limit    %Used   File Usage       Limit   %Used |
| /home1              2.0      10.0    19.52        46696      200000   23.35 |
| /work             807.4    1024.0    78.85      2742645     3000000   91.42 |
| /scratch        23904.2       0.0     0.00     11820127           0    0.00 |
-------------------------------------------------------------------------------
```

## Plan

For the research purpose, we have the following data:
1. the models, which are used to run in Specfem and for visulization. (~50 GB)
2. the data, we should keep the raw data and the processed data. (raw data: ~1 TB)
3. the sync result. Now I have these different types of sync:
    + 484 events for the hybrid model. (each iteration takes the 0.5 TB space)
    + 30 events for validation models. (total ~100 GB space each iteration)
    + several events for the cmt correcction. (~200 events for each iteration. 8x space than sync, so about 1.6T)

Assume we will run 20 iterations, then the total space will be:
1. The models, 50GB.
2. The data, 1TB.
3. The sync, since we will use ~200 events in each iteration, the total will be 4 TB.
4. The validation, since we will do that in each 5 iterations, the total will be 6.4 TB.
5. Kernels and Line search? COnsider them in the future.

So we will need about 12 TB space or more. So we should store any of us data in ICER's research directory and compress them accordingly. (use asdf)

As for the stampede2, we have only ~1T space. This is good for placing all the working directories. (only the structure of running specfem, and we can
place the output and DATABASE_MPI in the scratch directory)

## The data structure.

### ICER
+ /mnt/home/xiziyi 
    - anaconda
    - bin
    - data
    - package
    - script
    - temp
    - test
+ /mnt/research/seismolab2/japan_slab
    - cmts
    - data
    - models
    - sync
    - relocation

For the data directory, we should place the directories as:

- raw (the seed files, should be renamed according to the gcmt id)
    + fnet
    + cea
    + kma
    + fdsn
- processed (after having preprocessed)
    + bandpass_10s_120s
    + bandpass_20s_120s 
    + bandpass_40s_120s

For the sync directory, we have:

- hybrid
    + first_iteration (sync should have the similar structure with data)
    + ...
- validation
    + EARA2014 (have the same structue with the hybrid)
    + FWEA18
    + ...

For the relocation directory, we have:

- depth (as we may have other types of relocation)
    + frist_relocation_for_xxx_iteration. (asdf files are named according to there depth, also ln the 0 depth to the sync)