---
permalink: /
title: "Kunting Qi"
excerpt: "My research focuses on high-performance computing and its applications, especially collective communication for parallel programs."
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

I’m a PhD student in computer science at the University of Illinois Chicago, advised by Prof. Sidharth Kumar. My research focuses on **high-performance computing (HPC) and its applications**.

[Résumé (PDF)](/files/Kunting_Qi_Resume_HPC.pdf)

## Research

I design, implement, and tune **collective communication algorithms** that let groups of processes or GPUs exchange data. The best way to move that data depends on the machine and on who needs to send how much to whom. I use performance measurements and machine learning to help communication libraries choose an algorithm that fits the workload.

I also work on the applications that use these collectives. In large language model inference, GPUs exchange tokens as they route them to different experts. In graph analytics, processes exchange newly discovered relationships as a query runs. I study these communication patterns and measure how a change in the underlying algorithm affects the time it takes to run the whole application. [PhD research projects](/portfolio/)

## Background

I earned master’s degrees in computer science and statistics at Miami University. During research internships at Argonne National Laboratory in 2025 and 2026, I worked on tuning MPI collective operations. [Pre-PhD projects](/pre-phd/) · [CV](/cv/)
