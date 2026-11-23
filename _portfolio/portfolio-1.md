---
title: "Autotuning non-uniform MPI all-to-all communication"
excerpt: "In a graph computation, the amount of data each process sends can change with every iteration. Our tuner uses the observed message sizes to choose how MPI exchanges that data."
collection: portfolio
stage: phd
order: 4
advisor: Prof. Sidharth Kumar
---

In a distributed graph search, a process might discover thousands of new paths in one iteration and just a handful in the next. Each process uses `MPI_Alltoallv` to send those discoveries to the processes that need them. The fastest way to exchange the data depends on how many processes participate and how unevenly the messages are distributed.

We benchmarked the standard collective and two specialized all-to-all algorithms, varying their parameters, the number of processes, and the message sizes. We trained a model to predict communication time and used its predictions to build a lookup table. At each exchange, our C++ implementation uses summary statistics of the messages to select an algorithm and its settings.

On a 1,024-rank transitive-closure run on Polaris, the tuned exchange took 1.91 seconds, down from 11.52 seconds with the standard collective. The full application ran in 69.49 seconds, down from 79.50 seconds. [HiPC 2025 paper, Table VI (PDF)](https://kokofan16.github.io/assets/papers/HiPC25.pdf)

![Matrix showing how message sizes vary between pairs of MPI processes](/images/MPI_nonuniform.png)

[Presentation slides (PDF)](https://sidharthkumar.io/publications/HiPC_slides.pdf) · [Earlier project poster (PDF)](https://www.evl.uic.edu/documents/kunting.pdf)
