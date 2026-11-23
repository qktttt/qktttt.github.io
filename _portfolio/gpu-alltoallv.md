---
title: "GATAv for GPU all-to-all communication"
excerpt: "Mixture-of-experts models send different numbers of tokens to each GPU. GATAv groups small transfers within each node to reduce the number of messages crossing the network."
collection: portfolio
stage: phd
order: 0
---

In a mixture-of-experts model, each token goes to a few expert networks. When those experts run on different GPUs, the system has to send token activations to their destinations and return the results. The number of tokens going to each GPU changes from one batch to the next. I’m studying how to make this variable-size all-to-all exchange faster on Polaris and Aurora.

GATAv takes advantage of the fast links between GPUs on the same node. Before sending data across the network, GPUs write small blocks into a shared destination buffer on a local GPU. That GPU can send the blocks together. Large transfers go directly to their destinations, with a limit on how many sends can be in flight at once.

On Polaris, I tested the implementation on up to 512 GPUs. In a 32-GPU irregular exchange with a nominal size of 256 bytes per peer, the median exchange took **39.7 µs** with GATAv and **171.6 µs** with NCCL, the fastest baseline in that test.

On Aurora, I also measured the effect on three DeepSeek-R1 expert layers across 12 nodes (144 GPU tiles). At 64 tokens per rank, with MPICH’s HMEM option disabled for both runs, the mean of the three layer timings was **4.73 ms** with GATAv and **8.83 ms** with direct sends and receives. Each layer timing includes token dispatch, expert computation, and the return exchange.
