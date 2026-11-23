---
title: "Autotuning MPI broadcast in MPICH"
excerpt: "MPICH can silently switch broadcast algorithms or invoke another collective inside a broadcast. We traced those choices so the autotuner learns from the code that actually runs."
collection: portfolio
stage: phd
order: 1
---

An MPI broadcast sends data from one process to every process in a group. To train an autotuner, we need to know how long each broadcast algorithm takes. That measurement can be misleading in MPICH. If a configuration violates an algorithm’s restrictions, the library can silently run a fallback. If the algorithm calls another collective, its measured time also depends on how that inner call is tuned.

We grouped configurations by which algorithms they support and trained a separate model for each group. We first tuned algorithms that run independently. With that policy in place, we measured the algorithms that make nested calls and used those measurements to train the final broadcast policy.

In our Polaris benchmarks, the final policy sped up individual broadcasts by up to 30.71× over default MPICH and up to 2.76× over the ACCLAiM autotuner. [ExaMPI 2026 paper in the SC26 proceedings](https://sc26.supercomputing.org/proceedings/workshops/workshop_pages/ws_exampi107.html)
