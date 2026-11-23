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

## Internships

- **Summer 2026** — PhD Research Intern, Argonne National Laboratory. I worked with the MPICH team on autotuning MPI broadcasts.
- **Summer 2025** — PhD Research Intern, Argonne National Laboratory. I built a runtime tuner for non-uniform MPI all-to-all communication.
- **Summer 2018** — Software Developer Intern, Infervision, Beijing. I developed backend software for storing CT images.

## Education

- **2028 (expected)** — PhD in Computer Science, University of Illinois Chicago.
- **2024** — MS in Statistics, Miami University.
- **2023** — MS in Computer Science, Miami University.
- **2020** — BS in Computer Science, cum laude, Miami University.

[Pre-PhD projects](/pre-phd/) · [CV](/cv/)
