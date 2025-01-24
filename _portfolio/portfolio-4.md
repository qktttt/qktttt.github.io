---
title: "Serial Interval Estimation for COVID-19"
excerpt: "Developed a robust method combining kernel-based imputation and Hamiltonian Monte Carlo to accurately estimate COVID-19 serial intervals from incomplete datasets. <br/> "
collection: portfolio
--- 

Advised by Prof. Jing Zhang (Miami University, Department of Statistics)

## Introduction
The serial interval (SI) measures the time between symptom onset in an infector and their infectee. Accurate estimation of SI is crucial for understanding disease transmission, predicting epidemic trends, and informing public health policies. However, real-world COVID-19 datasets often have missing or incomplete information, such as unknown infection links and unrecorded symptom onset dates, making SI estimation challenging. This project develops a refined method to address these issues by imputing missing data and improving computational efficiency.

## Methodology
In this project, I designed a method to estimate SI by imputing missing links within infection networks and integrating this with a Hamiltonian Monte Carlo (HMC) Bayesian sampler. This approach estimates the posterior distribution of the generation interval (GI) mean and standard deviation, which are essential for calculating the SI. Key features include:

1. **Imputation of Missing Links**: A kernel-based method was developed to probabilistically infer missing links in the infection network. This ensures a more accurate representation of the underlying transmission dynamics.
   
2. **Integration with HMC Sampler**: To address computational inefficiencies in large-scale datasets, the imputation process is combined with HMC. This significantly reduces the computational cost while ensuring robust posterior estimation of the GI parameters.

3. **Handling Negative Serial Intervals**: The methodology incorporates negative SI values, which occur when infectees exhibit symptoms earlier than their infectors, while ensuring unbiased estimation.

## Data
I analyzed eight COVID-19 datasets collected from:
- Government websites.
- Published studies.
- Official social media platforms such as Weibo and Twitter.

The datasets include information on multiple variants (e.g., Delta, Omicron) and cover different geographic regions. Despite their breadth, these datasets are often incomplete, necessitating the use of imputation techniques.

<!--**[Placeholder for Data Overview Figure or Table]**-->

## Challenges
Several challenges arose during this project:
- **Data Completeness**: Many datasets lacked infector-infectee relationships or precise symptom onset dates, requiring advanced imputation techniques.
- **Computational Demand**: Large-scale datasets posed significant computational challenges, which were mitigated by transitioning to the HMC algorithm.
- **Variability in Data Quality**: Differences in data collection methods across regions complicated standardization and analysis.

## Results
Simulation studies demonstrate that the proposed method improves estimation accuracy compared to traditional approaches. The integration of imputation with HMC reduces bias and narrows credible intervals for GI parameters, even in datasets with a high proportion of missing information.

<!--**[Placeholder for Simulation Results Figure]**-->

The method was applied to real-world COVID-19 datasets to estimate the SI for various variants. Results show consistent performance and highlight the method's adaptability across different epidemiological contexts.

<!--**[Placeholder for Real-World Results Figure]**-->

## Conclusion
This project presents a robust framework for estimating the serial interval in the presence of incomplete data. By combining a kernel-based imputation method with an HMC Bayesian sampler, the approach addresses key challenges in SI estimation, improving both accuracy and computational efficiency. Future work will focus on further validating the method with additional datasets and extending its application to other infectious diseases.

<!--**[Placeholder for Conclusion Figure, if applicable]**-->
