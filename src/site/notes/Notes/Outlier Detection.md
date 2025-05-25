---
{"topic":"DataScience","dg-publish":true,"permalink":"/Notes/Outlier Detection/","dgPassFrontmatter":true,"noteIcon":""}
---

## Univariate outer detectors
### Z-score / Standard Score
- commonly, values with Z-scores beyond a threshold (e.g., ±3) are considered outliers
### Interquartile Range (IQR) Method
- Values below $Q1− 1.5 \times \text{IQR}$ or above $Q3+1.5 \times \text{IQR}$ are considered outliers.

## Multivariate outer detectors
### Mahalanobis Distance
- Measures the distance of a point from the mean of a multivariate distribution, considering correlations among variables 
- Higher values of the Mahalanobis distance indicate potential outliers
### PCA
- see [[Notes/Dimensionality Reduction#**PCA** vs. **LDA**\|Dimensionality Reduction#**PCA** vs. **LDA**]]
- identify data points that deviate from the pattern of the majority after transformation
### Elliptic Envelope (Robust Covariance)
- fits an elliptical envelope to the data and classifies points outside it as outliers, assuming a Gaussian distribution
### FPOF (Fixed-Point Outlier Factor)
- a density-based outlier detection method: detect outliers by comparing the density of each point with those around it
- outlier = a point has a significantly lower count within a fixed radius 
### Counts Outlier Detector
- tracks how frequently each data point or observation appears in the dataset
- outlier = points with unusually low or high counts (depending on the context) 
- suitable for categorical data or discrete datasets
### Distance Metric Learning
-  supervised or semi-supervised learning to label outliers
- aims to learn an optimal distance metric (often a Mahalanobis distance or similar) that maximizes the separation of normal and anomalous points based on certain criteria or labeled examples of outliers
- perform well on complex or high-dimensional data
### Shared Nearest Neighbors (SNN)
- a graph-based approach that calculates the similarity between each pair of data points by examining how many neighbors they share
- outlier = points with few or no shared neighbors in common with other points
- perform well on complex or high-dimensional data

### Doping
- a strategy that introduces synthetic samples ("doped points" or "artificial outliers") into the dataset to help train a model to better distinguish between normal data points and anomalies