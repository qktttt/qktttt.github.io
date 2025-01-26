---
title: "Optimization of Non-uniform MPI Collective Communication with Machine Learning"
excerpt: "Developing a machine learning-based system to predict and optimize the performance of MPI non-uniform all-to-all communication under various configurations and workloads.  <br/> "
collection: portfolio
advisor: Prof. Sidharth Kumar
---

**Advised by: Prof. Sidharth Kumar (University of Illinois Chicago, Department of Computer Science)**

(In preparation for submitting to IEEE Cluster Conference 2025)

# Performance Optimization of Non-Uniform MPI All-to-All Communication

## Introduction
Non-uniform MPI all-to-all communication is when each process sends and receives different amounts of data from other processes, unlike uniform communication where data sizes are the same. It is commonly used in parallel computing, but its performance depends on the workload, algorithms, and settings. There are multiple different algorithms for non-uniform MPI all-to-all communication, and there are numerous parameters need to be specified when using these algorithms. 

In parallel applications, data exchange between processes can take a lot of time. Creating a system to choose the best algorithm and settings for this is an ongoing goal. Right now, people rely on fixed rules to pick algorithms and settings, but this approach is not flexible or reliable, especially for non-uniform MPI all-to-all communication.

In this project, we used supervised machine learning to build a system that predicts how well different algorithms perform with different settings for non-uniform MPI all-to-all communication. The system uses these predictions to automatically choose the best algorithm and settings for a given workload. This machine learning approach replaces fixed rules, making the system more flexible and better at handling different workloads and network conditions, which helps improve the performance of parallel applications.

![Alt text](images/MPI_nonuniform.png)
*In real-world parallel applications, the number of elements sent between processes can vary. The time it takes to exchange data between pairs of processes can also differ, and network conditions can add more variation. These factors make MPI all-to-all communication uneven and challenging to optimize.*

## Methodology
The figure as shown in the following show our general workflow for this project. 
![Alt text](images/mpi_workflow.png)

### Benchmarking
To train a performance prediction model, we conducted extensive benchmarks of MPI non-uniform all-to-all communication under various scenarios. These benchmarks included different combinations of processes, algorithms, and parameter settings. We used the Polaris supercomputer at Argonne National Laboratory (ANL) because it provides a large-scale computing environment, fast interconnects, and reliable hardware. This allowed us to collect accurate data under realistic conditions, which is essential for understanding performance and training predictive models.

### Machine Learning Model
With benchmarked data, we fit machine learning models to predict the performance of MPI non-uniform all-to-all operations. The models take workload and configuration information as input and output predictions of communication time. Several machine learning techniques were evaluated, and the most accurate models were selected for further analysis. To improve the model's accuracy, data preprocessing techniques such as transformation are applied before model fitting.

### Optimization Mechanism
The goal of the optimization mechanism is to leverage the predictive power of the machine learning model to determine optimal configurations for MPI non-uniform all-to-all communication. We are exploring two approaches for this:
1. **Lookup Table**: Precomputing recommendations for common scenarios to enable fast decision-making during runtime.
2. **Real-Time Model Integration**: Using the trained machine learning model to provide adaptive recommendations for unseen scenarios.

The created system will be deployed in the real parallel application for real-world evaluation. 

## Results
Preliminary results show that the machine learning models can accurately predict performance under a variety of scenarios. These predictions form the basis of the proposed optimization mechanism, which is currently under development.

## Conclusion
This project develops a machine learning-driven approach to optimize MPI non-uniform all-to-all communication. By predicting performance and leveraging those predictions to suggest optimal configurations, the proposed system has the potential to significantly improve communication efficiency in parallel computing. Future steps involve refining the optimization mechanism and further validating the system.

****
