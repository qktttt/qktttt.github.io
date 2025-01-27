---
title: "Datanugget - Python Version"  
excerpt: "The Python implementation of the Datanugget package, achieving at least a 500% improvement in speed and capacity compared to the original R version.<br/> 
<img src='/images/datanugget_teaser.png'> 
*(Figure adapted from [1])*" 
collection: portfolio
advisor: "Prof. Javier Cabrera"
---

**Advised by: Prof. Javier Cabrera (Rutgers University, Department of Statistics)** 

## 1. Introduction
Large datasets with millions of observations pose significant challenges for analysis, as traditional methods require substantial computational resources and memory. Techniques like clustering or PCA often become impractical due to their high time and space complexity, particularly with high-dimensional data. Random sampling is a common approach to reduce dataset size, but it often leads to the loss of critical information, such as small clusters or edge patterns, while introducing high variability in outcomes. Thus, a method that balances computational efficiency with the preservation of essential information is critically needed. 

## 2. Background
The **Datanugget** R package [2] efficiently represents large datasets while preserving their structural and statistical properties by partitioning the data into smaller, weighted units called **data nuggets**. Each nugget represents a cluster of observations with similar characteristics and is characterized by three key attributes: **center**, **weight**, and **scale**, which collectively capture the variability and distribution of the data [1].

The Datanugget package reduces large datasets into a manageable number of nuggets, enabling the application of weighted statistical methods and modeling directly on the summarized data. These methods include unsupervised approaches (e.g., weighted PCA, weighted clustering) and supervised methods (e.g., generalized linear models, linear regression). 

![Data Nugget Workflow](/images/datanugget_teaser.png "Data Nugget Creation and Refinement (Adapted from [1])")  
*The workflow involves two phases: nugget creation and refinement ([1]).* 

**Nugget Creation Phase**  
The goal is to reduce a large dataset into smaller, representative units called nuggets. Each nugget summarizes a subset of the data using three properties:  
1. **Center**: The central point of the subset (e.g., mean or centroid).  
2. **Weight**: The number of original observations in the nugget.  
3. **Scale**: The variability or spread within the nugget.  

**Nugget Refinement Phase**  
The initial nuggets are refined by splitting oversized or high-variability nuggets to improve granularity and structural accuracy. 


## 3. Challenge
The Datanugget R package, while effective in reducing datasets and preserving structural properties, faces limitations in speed and capacity when processing extremely large datasets (e.g., millions of observations). On consumer-grade hardware, execution can become prohibitively slow or fail due to memory constraints. These limitations stem from the computational overhead of partitioning large datasets into nuggets, which scales poorly with dataset size. 

More details regarding the methodology of Datanugget can be found in [1].

## 4. Contribution
In this project, we developed **Datanugget-Python**, a Python-based implementation optimized for speed and capacity. This version efficiently handles datasets with tens of millions of observations on consumer-grade computers, overcoming the performance limitations of the original R package. 

By leveraging Python’s numerical computing libraries (e.g., `numpy`, `scipy`) and parallel processing tools, the package achieves significant speed improvements while preserving data integrity and statistical properties. 

**Key Results**:  
1. Achieved an **average speedup of 562.2%** over the original R package. 
2. Successfully processed **50 million observations with 10 variables** on a desktop computer with 32 GB RAM. 

**A ready-to-use Python package, demos, and documentation will be released soon.** 

---

### References  
1. Beavers, Traymon E., et al. "Data Nuggets: A Method for Reducing Big Data While Preserving Data Structure." *Journal of Computational and Graphical Statistics* (2024): 1–21.  
2. Beavers T, Cabrera J, Cheng G, Qi K, Lubomirski M (2024). *datanugget: Create and Refine Data Nuggets*. R package version 1.3.1. Available at: [https://CRAN.R-project.org/package=datanugget](https://CRAN.R-project.org/package=datanugget).