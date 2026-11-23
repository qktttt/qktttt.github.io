---
permalink: /
title: "Kunting Qi"
excerpt: "Computer science PhD student at the University of Illinois Chicago studying GPU communication, MPI autotuning, and parallel Datalog."
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

I’m a computer science PhD student at the University of Illinois Chicago, where I work with Prof. Sidharth Kumar on high-performance computing. I study how parallel programs spend their time moving data and how to make those exchanges cheaper when the workload changes.

## Current research

**GPU communication.** In a mixture-of-experts model, each token may need to reach an expert on a different GPU. My GATAv project groups small transfers headed to the same node. I benchmark the exchange on Polaris and measure its effect on expert-layer runtime on Aurora. [GATAv project](/portfolio/gpu-alltoallv/)

**MPI autotuning.** I use performance measurements to choose communication algorithms at runtime. For all-to-all exchanges, the distribution of message sizes helps predict which algorithm will be fastest. For broadcasts, the tuner also needs to know which algorithm MPICH actually ran when it collected a timing. [Non-uniform all-to-all](/portfolio/portfolio-1/) · [Broadcast in MPICH](/portfolio/mpi-broadcast/)

**Parallel Datalog.** Graph and program-analysis queries often join several relations at once. My collaborators and I study how to find the matches while keeping intermediate results small enough to fit in GPU memory and limiting the data exchanged between cluster nodes. [GPU joins](/portfolio/gpu-datalog/) · [Distributed joins](/portfolio/distributed-datalog/)

## Background

I earned master’s degrees in statistics and computer science at Miami University. My interests in statistical and numerical computing grew out of that work. [Pre-PhD projects](/pre-phd/) · [CV](/cv/)
