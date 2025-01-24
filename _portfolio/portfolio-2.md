---
title: "Optimization of Non-uniform MPI Collective Communication with Machine Learning"
excerpt: "Developing a machine learning-based system to predict and optimize the performance of MPI non-uniform all-to-all communication under various configurations and workloads.  <br/> "
collection: portfolio
advisor: Prof. Sidharth Kumar

---

Advised by: Prof. Sidharth Kumar (University of Illinois Chicago, Department of Computer Science)

# Performance Optimization of Non-Uniform MPI All-to-All Communication

## Introduction
Non-uniform MPI all-to-all communication is widely used in parallel computing applications, but its performance is highly dependent on workload characteristics, algorithm choices, and parameter configurations. This project aims to address these challenges by developing a machine learning-based system to predict performance and optimize configurations for MPI non-uniform all-to-all communication.

## Methodology

### Benchmarking
To train a performance prediction model, we conducted extensive benchmarks of MPI non-uniform all-to-all communication under various scenarios. These benchmarks include different combinations of processes, algorithms, and parameter settings. The collected data provides a foundation for understanding performance trends and training predictive models.

### Machine Learning Model
We developed machine learning models to predict the performance of MPI non-uniform all-to-all operations. The models take workload and configuration information as input and output predictions of communication time. Several machine learning techniques were evaluated, and the most accurate models were selected for further analysis. To improve the model's accuracy, data preprocessing techniques such as transformations were applied.

### Optimization Mechanism
The goal of the optimization mechanism is to leverage the predictive power of the machine learning model to determine optimal configurations for MPI non-uniform all-to-all communication. We are exploring two approaches for this:
1. **Lookup Table**: Precomputing recommendations for common scenarios to enable fast decision-making during runtime.
2. **Real-Time Model Integration**: Using the trained machine learning model to provide adaptive recommendations for unseen scenarios.

The final choice between these approaches is still under evaluation.

## Results
Preliminary results show that the machine learning models can accurately predict performance under a variety of scenarios. These predictions form the basis of the proposed optimization mechanism, which is currently under development.

## Conclusion
This project develops a machine learning-driven approach to optimize MPI non-uniform all-to-all communication. By predicting performance and leveraging those predictions to suggest optimal configurations, the proposed system has the potential to significantly improve communication efficiency in parallel computing. Future steps involve refining the optimization mechanism and further validating the system.

<!--**[Placeholder for Figures: Benchmarking Setup, Model Performance]**-->
