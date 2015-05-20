---
title: "Tutorial for Greg's fabulous peeps"
layout: post
date: 'May 20th, 2014'
category: Tutorial
tags:
  - molecular ecology
  - hpcc
  - QIIME
  - mothur
---

# Getting started
- stuff
- stuff
- more stuff

# Getting to know MSU's HPCC
- MSU's HPCC uses a qsub system
- In order to keep packages organized, tools are loadable in modules.  Here is a [list of all of the installed packages (modules) on the HPCC](https://wiki.hpcc.msu.edu/display/hpccdocs/Installed+Software).  Bioinformatics software is [listed here](https://wiki.hpcc.msu.edu/display/hpccdocs/Installed+Software#InstalledSoftware-BioinformaticsSoftware).  Let's look for QIIME and mothur on the list.

To see which modules you have loaded on the HPCC, just type `module list` -- this is what I see when I do this:

```
```


- more stuff

# Using QIIME and mothur

1. First, let's search for QIIME by typing `module spider qiime`.  You should see this:

```
$ module spider qiime<br>Using system spider cache file

--------------------------------------------------------------------------------

##   QIIME:

 Versions:
    QIIME/1.4.0
    QIIME/1.5.0
    QIIME/1.6.0
    QIIME/1.7.0
    QIIME/1.8.0
    QIIME/1.9

--------------------------------------------------------------------------------

  To find detailed information about QIIME please enter the full name.<br>  For example:

 $ module spider QIIME/1.9

--------------------------------------------------------------------------------

```

The last fully installed version of QIIME on the HPCC is version 1.7.0 -- some of the tools I use are in versions which are not fully compiled (i.e. versions 1.8.0 and 1.9.0).  

Let's load QIIME/1.7.0 by typing `module load QIIME/1.7.0` and then `module list` to see what is installed:
```

$ module list<br>Currently Loaded Modules:
  1)  GNU/4.4.5             16) GSL/1.15             31) pplacer/1.1.alpha13r2
  2)  OpenMPI/1.4.3         17) mothur/1.25.0        32) ChimeraSlayer/20110519
  3)  TBB/4.1.0             18) USEARCH/5.2.236      33) cdbtools/1.0
  4)  CMake/2.8.5           19) rtax/0.983           34) RDPClassifier/2.9
  5)  MATLAB/R2015a         20) raxml/7.3.0          35) gdata/2.0.17
  6)  Stata/13.0            21) MUSCLE/3.8.31        36) qcli/0.1.0
  7)  powertools/1.2        22) uclust/1.2.22q       37) biomformat/1.2.0
  8)  QIIME/1.7.0           23) infernal/1.0.2       38) NumPy/1.6.1
  9)  PyCogent/1.5.3        24) CDHIT/4.6.1c         39) pyqi/0.2.0
  10) BLAST/2.2.22          25) PyNAST/1.2           40) dateutil/1.5
  11) BLAT/35               26) matplotlib/1.1.0a    41) R/3.0.1
  12) bwa/0.7.7.r441        27) Python/2.7.2         42) Boost/1.52.0
  13) SAMTools/0.1.19       28) FastTree/2.1.7       43) MKL/11.1
  14) mpi4py/1.3            29) clearcut/1.3         44) emperor/0.9.1
  15) AmpliconNoise/1.25    30) ParsInsert/1.04
```

We're going to need all these tools to run QIIME (and parts of mothur) -- this is partly why installing QIIME is so difficult.  Installing the actual QIIME package is not so problematic, but getting all the dependencies to talk to one another is difficult.

Let's load version 1.9.0 (which is listed as 1.9 on the HPCC) by typing: `module load QIIME/1.9`
and then `module list`.  You should see something like this:

```
$ module list
Currently Loaded Modules:
  1) GNU/4.4.5        4) CMake/2.8.5      7) powertools/1.2    10) uclust/1.2.22q
  2) OpenMPI/1.4.3    5) MATLAB/R2015a    8) QIIME/1.9         11) Biopython/1.61
  3) TBB/4.1.0        6) Stata/13.0       9) Python/2.7.2      12) GSL/1.15
```

The newest OTU picking technique for Illumina sequencing is included with QIIME 1.9.0 and described in this paper: [Subsampled open-reference clustering creates consistent, comprehensive OTU definitions and scales to billions of sequences](https://peerj.com/articles/545/).
- stuff
- stuff
- more stuff
