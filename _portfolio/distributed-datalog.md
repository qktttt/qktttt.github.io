---
title: "Distributed Datalog with worst-case optimal joins"
excerpt: "We built a Datalog engine that keeps multi-way joins local to each MPI process and exchanges newly derived facts between iterations. We evaluated it on Aurora and Polaris."
collection: portfolio
stage: phd
order: 2
---

A graph query that looks for triangles can generate a long list of two-edge paths before checking which paths close into triangles. On a cluster, storing and moving those partial matches can dominate the query. Our Datalog engine uses worst-case optimal joins to check constraints one variable at a time. The challenge is getting the relevant facts onto the same process as recursive rules keep producing new ones.

We arranged MPI processes in a multidimensional grid and partitioned each relation by the variables it contains. Each process can then perform its joins locally. After each round, the engine redistributes only the newly derived facts and reuses the same grid for the next round.

We evaluated graph-mining and program-analysis workloads on Argonne’s Aurora and Polaris supercomputers. The grid shape mattered even for the same query. A two-dimensional grid ran the Orkut triangle query faster when memory allowed. At 32 processes on Polaris, only the three-dimensional grid fit in memory. [October 2026 preprint](https://arxiv.org/abs/2610.12692)
