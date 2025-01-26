---
title: "Datanugget - Python version"
excerpt: "The Datanugget package developed in python, compared to original Datanuget package implemented in R, the capacity and speed are improved by at least 500%<br/><img src='/images/datanugget_teaser.png'>"
collection: portfolio
advisor: "Prof. Javier Cabrera"
---

Advised by: Prof. Javier Cabrera (Rutgers University, Department of Statistics)

Large datasets with millions of observations present significant challenges for analysis, as traditional methods require substantial computational resources and memory. Techniques like clustering or PCA often become impractical due to their high time and space complexity, particularly with high-dimensional data. Random sampling is a common approach to reduce dataset size but frequently results in the loss of critical information, such as small clusters or edge patterns, while introducing high variability in outcomes. Therefore, a method that provides both computational efficiency with the preservation of essential information is highly needed.

The **Datanugget** R package [2] is designed to efficiently represents large datasets while preserving their structural and statistical properties. It accomplishes this by partitioning the data into smaller, weighted units called "data nuggets." Each nugget represents a cluster of observations with similar characteristics and is described by three key attributes: **center**, **weight**, and **scale**, which collectively capture the variability and distribution of the data [1].

The Datanugget package reduces large datasets into a more manageable number of nuggets, enabling the application of weighted statistical methods and modeling directly on the summarized data. These weighted methods include both unsupervised approaches, such as weighted PCA and weighted clustering, and supervised methods, including generalized linear models, linear regression, and others.

![Alt text](/images/datanugget_teaser.png "Optional Title") (This figure is referenced from [1])
*For Datanugget, there are two phase, as shown in the above figure, one phase is the creation of data nuggets and another phase is the refinement for the created nuggets*

*In the nugget creation phase, as shown in the above figure,the goal is to reduce a large dataset into smaller, representative units called nuggets. Each nugget summarizes a subset of the data using three key properties:*
1. *Center: Represents the central point of the subset (e.g., mean or centroid).*
2. *Weight: Reflects the number of original observations in the nugget.*
3. *Scale: Captures the variability or spread of the data within the nugget.*

*In the nugget refinement phase, the initial nuggets are analyzed to ensure they accurately represent the dataset’s structure. Nuggets that are too large, have high variability, or are elongated are split into smaller nuggets for better granularity.*

The Datanugget R package, while effective in reducing large datasets and preserving their structural properties, faces significant limitations in speed and capacity when handling extremely large datasets, such as those with millions of observations. On consumer-grade computers, the execution can become prohibitively slow, often failing to complete due to memory constraints. These limitations stem from the computational overhead required to partition and process large datasets into data nuggets, which increases significantly with dataset size.

In this project, we create **Datnugget - Python version**, focusing on optimizing its speed and capacity. The new Python-based package has been designed to handle large-scale datasets over millions of observations efficiently, overcoming the performance and memory limitations of the original R implementation. 

By leveraging Python's robust libraries for numerical computing and parallel processing, the package achieves significantly faster execution while maintaining the structural integrity and statistical properties of the data. This enhanced version enables the practical application of data nugget techniques on consumer-grade computers for large-scale datasets, making it a more scalable and accessible tool for big data analysis.

Our initial experiments shows that, compared to the original R package, our Python version Datanugget package:
1. Has an average speedup of %562.2 over the original R package. 
2. One a desktop computer with 32 Gigabytes, the Python version package can process data of 50 millions observations with 10 variables

**More details, ready-to-use Python package and demo will be available soon.**

Reference
======
1. Beavers, Traymon E., et al. "Data Nuggets: A Method for Reducing Big Data While Preserving Data Structure." Journal of Computational and Graphical Statistics just-accepted (2024): 1-21.
2. Beavers T, Cabrera J, Cheng G, Qi K, Lubomirski M (2024). _datanugget: Create, and Refine Data Nuggets_. R package version 1.3.1, <https://CRAN.R-project.org/package=datanugget>.