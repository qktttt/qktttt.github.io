---
permalink: /
title: "Kunting Qi"
excerpt: "Computer science PhD student at the University of Illinois Chicago studying GPU communication, MPI autotuning, and parallel Datalog."
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

I’m a PhD student in computer science at the University of Illinois Chicago, advised by Prof. Sidharth Kumar. I work on high-performance computing and distributed systems, with a focus on GPU communication and MPI collectives. I build and benchmark communication algorithms for workloads where the amount of data moving between processors changes from one iteration to the next.

[Résumé (PDF)](/files/Kunting_Qi_Resume_HPC.pdf)

## GPU communication and query engines

I’m developing GATAv, a CUDA and SYCL implementation of variable-size all-to-all communication for GPU clusters. On Argonne’s Polaris and Aurora supercomputers, I study how GPUs can exchange the tokens that a mixture-of-experts model routes to different experts. I also integrate the collective into vLLM to measure its effect on DeepSeek-R1 decoding. [GATAv project, figures, and slides](/portfolio/gpu-alltoallv/)

My Datalog work tackles a related problem in graph and program analysis. On a GPU, I co-developed join kernels that spread the work of frequent keys across thread blocks. On a cluster, I built an MPI engine that places related records on the same rank so that multi-way joins can run locally. We evaluated the distributed engine on up to 2,048 processes. [GPU Datalog](/portfolio/gpu-datalog/) · [Distributed Datalog](/portfolio/distributed-datalog/)

## Research at Argonne

During my summer 2025 internship with Dr. Venkatram Vishwanath and Prof. Michael Papka, I built a C++ autotuner for non-uniform MPI all-to-all exchanges. Our work received the HiPC 2025 Distinguished Paper Award. In summer 2026, I joined Argonne’s MPICH team, working with Dr. Hui Zhou and Dr. Rajeev Thakur on a tuner that accounts for which broadcast algorithm actually executes. We presented that work at ExaMPI at SC26. [HiPC project](/portfolio/portfolio-1/) · [ExaMPI project](/portfolio/mpi-broadcast/)

## Education

I began my PhD in August 2024 and expect to finish in August 2028. At Miami University, I earned an MS in statistics (2024), an MS in computer science (2023), and a BS in computer science, cum laude (2020). [Pre-PhD projects](/pre-phd/) · [CV](/cv/)
