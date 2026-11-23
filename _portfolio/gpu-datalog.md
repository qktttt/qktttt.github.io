---
title: "Worst-case optimal joins for Datalog on GPUs"
excerpt: "We developed SRDatalog to evaluate multi-way joins on a GPU, where large temporary results can exhaust device memory and unevenly distributed keys can leave processors idle."
collection: portfolio
stage: phd
order: 3
---

Program-analysis rules often match facts from several relations at once. Evaluating those matches two relations at a time can fill GPU memory with partial results that the final rule discards. In SRDatalog, we use worst-case optimal joins to intersect candidate values one variable at a time.

Making that algorithm effective on a GPU requires balancing the work. A frequent key can leave one group of threads with far more candidates to check than its neighbors. We use a histogram of key frequencies to distribute that work, store relations in flat columns, and size output buffers in two phases. These choices address both uneven execution time and limited device memory.

On the disassembly-analysis benchmark for Z3, SRDatalog processed 126.9 million input facts in 2.00 seconds on one NVIDIA RTX 6000 Ada GPU. The same workload took 24.4 seconds in Ascent on 32 CPU cores. [April 2026 preprint, Table 2](https://arxiv.org/abs/2604.20073)
