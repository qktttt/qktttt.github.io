---
title: "Multi-Objective Optimization for Corn Planting Scheduling"
excerpt: "  Optimized corn planting schedules using LSTM-based GDU prediction and multi-objective genetic algorithms to minimize waste and improve harvest consistency. <br/><img src='/images/genetic algorithm.png'>
(Figure referenced from [2])"
collection: portfolio
advisor: Dr. Byran Smucker, Prof. Sundaramoorthi Durai
teammates: 
- Mingshi Cui
---

**Advised by: Dr. Byran Smucker (Henry Ford Health) and Prof. Sundaramoorthi Durai (Washington University in St. Louis, Olin Business School)**

**Teammates: Mingshi Cui (Rutgers University)**

Submitted Paper: [A Multi-Objective Capacity-Constrained Optimization of Corn Planting Scheduling](https://sites.miamioh.edu/byran-smucker/files/2024/05/Corn_Planting_Optimization_JORS.pdf)

**Award: Syngenta Corp Challenge 2021, 2nd Prize** 

## Introduction
Corn planting and harvesting schedules are essential for managing storage capacity and reducing waste. If planting schedules are not carefully planned, weekly harvest quantities can exceed storage limits, leading to wastage, or fall short, resulting in inefficiencies. The goal of this project is to develop a practical approach for scheduling corn planting that minimizes waste, ensures consistent harvests, and respects storage capacity constraints.

![Alt text](/images/corn.jpg "Optional Title")

This project builds on the 2021 Syngenta Crop Challenge, which asked participants to design better planting schedules for corn populations. The challenge involved predicting harvest times based on weather data and optimizing planting schedules to address storage limitations. 

## Background and Problem
![Alt text](/images/corn_process.png)

A corn seed population has a specific planting window, which defines the earliest and latest dates the seeds can be planted. After planting, the seeds require a certain amount of warmth, measured in Growing Degree Units (GDUs), to fully mature. Once mature, the corn can be harvested, and each seed population produces a certain number of corn ears.

The harvested corn will be stored in a storage facility with limited capacity. If the amount of corn harvested exceeds the storage capacity, the excess will be wasted. Without proper planning, there can be large fluctuations in harvest quantities. As shown in the following figure, sometimes, the harvest greatly exceeds the storage limit and causes wastage, while at other times, the harvest is much smaller than the capacity, leaving storage space unused. This imbalance leads to inefficiencies in both storage usage and harvest management.

![Alt text](/images/original.png)

The goal is to decide the exact planting dates for each corn seed population while minimizing the following three objectives at the same time:

The largest difference between weekly harvest amounts and storage capacity.
The median difference between weekly harvest amounts and storage capacity.
The number of weeks with non-zero harvest amounts.
To efficiently solve this problem, two key steps are required:

Predicting harvest time: For any given planting date, we need to calculate when the corn will reach maturity. This requires estimating the GDUs for each day to determine when the seed population will have enough warmth to be harvested.

Optimizing planting dates: With thousands of seed populations to manage, we need to find the best planting dates for all of them to minimize the three objectives above.

Minimizing these three objectives will help ensure an efficient harvest while staying within storage limits and spreading out the harvest weeks.

## Methodology
1. **Predicting GDUs**:  
   - Historical weather data from 2009 to 2019 was used to train a Long Short-Term Memory (LSTM) neural network for daily GDU predictions. 
   - The LSTM model was implemented using Python's Keras library, which provided a flexible and efficient platform for handling time-series data. These predictions allowed us to estimate when each corn population would be ready for harvest.

![Alt text](/images/gdu_prediction.png)
*The above fiture shows the daily GDU unit over a site over years 2008-2022. The green lines shows our LSTM prediction for daily GDU for 2020-2022, we can see our prediction accurately capture the seasonality of the data, and produce reasonable estimation for daily GDU.*

2. **Optimizing Planting Schedules**:  
   - A genetic algorithm was used to optimize planting dates for over 2,500 corn populations, implemented with the R `nsga2` package. This multi-objective algorithm was used to balance the following goals:
     - Minimize the median and maximum difference between weekly harvest quantities and storage capacity.
     - Reduce the number of weeks with non-zero harvests.
     - Minimize the amount of corn wasted due to exceeding storage limits.

   - The algorithm's flexibility allowed us to explore a wide solution space and identify effective planting schedules.

3. **Selecting the Best Solution**:  
Generally, Genetic Algorithm will generate a large number of solutions. Under multiple objectices, some solutions may be better than others on some objectives, and there is no simple best solution. To select the best solution: 
- we first compute the Pareto front of the solutions, which is a set of solutions that are not dominated by any other solution. 
- Then we use the hypervolume indicator and TOPSIS method to select the most balance and well-rounded solution from the Pareto front.

## Results
The framework was tested on real-world data provided by the Syngenta Crop Challenge. It successfully produced planting schedules that reduced waste, minimized weekly harvest variability, and improved storage efficiency compared to the baseline solutions. The LSTM model implemented in Python accurately predicted GDUs, and the genetic algorithm in R was effective at finding optimized schedules.

![Alt text](/images/optimized_solution.png)


The figure above shows the harvest quantities achieved using our method. Compared to the original approach, our method uses fewer harvest weeks, making the harvest schedule simpler. It also reduces the difference between weekly harvest quantities and storage capacity, both for the largest difference and the median difference. This helps prevent big fluctuations. Additionally, it greatly reduces the amount of corn wasted when the harvest exceeds storage capacity, making the process more efficient overall.

## Conclusion
This project provides a straightforward and practical method for optimizing corn planting schedules. By combining predictive modeling using LSTM and optimization techniques implemented in R, it addresses key challenges like inconsistent harvests and storage constraints. The approach can also be applied to similar agricultural scheduling problems, making it a useful tool for improving resource management and reducing waste.
