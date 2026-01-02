---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Centroid-based Clustering/","dgPassFrontmatter":true,"noteIcon":""}
---


>[!Source] 
>https://towardsdatascience.com/6-types-of-clustering-methods-an-overview-7522dba026ca


# What is Centroid-based Clustering

>Centroid-based methods group data points together based on the proximity of data points to the centroid (cluster center).

## Measure proximity
- **Euclidean distance**: Shortest (straight-line) distance, useful for numerical features, this is the default distance measure
- **Manhattan distance**: Sum of absolute differences, useful for categorical features
- **Hamming distance**: Percentage of bits that differ, useful for binary features
- **Mahalanobis distance**: Standardised form of Euclidean distance
- **Minkowski distance**: Generalized form of Euclidean and Manhattan distance
- **Chebyshev distance**: Maximum absolute difference
## Examples
- **K-Means clustering**
- **K-modes & K-prototype**
- **K-Medoids**
- **Mean Shift**
- **Fuzzy Clustering** (soft K-means; data points can be part of multiple clusters)
# K-Means Clustering

## How it works
1. Choose the number K of clusters
2. Select at random K points, the centroids (not necessarily from your dataset)
3. Assign each data point to the closest centroid => that forms K clusters
4. Compute and place the new centroid of each cluster
5. Reassign each data point to the new closest centroid
6. Repeat until your model is ready (i.e. cost function reaches minimum)

> - Actually, in K-means, the cost never increases.
> - Clustering algorithms such as KMeans have a difficult time accurately clustering data of high dimensionality (ie. too many features)

>[!Important]
>**K-Means Clustering vs. KNN ([[StudyNotes/K-Nearest Neighbor\|K-Nearest Neighbor]])**
>
>| K-means clustering | KNN |
>| -- | -- |
>| k = number of clusters | k = number of nearest neighbors |
>| unsupervised learning | supervised learning |
>| clustering | regression & classification |
>| to optimize, use elbow method | to optimize, use cross validation & confusion matrix |
>
## Tips during use
### Random Initialisation trap
- = the random centroids at the start may lead to inappropriate clustering
- solution: 
	- use more than more one random initialisation (50 - 1000)
	- K-Means++ (already implemented in python/R)
### Choose the right number of clusters
- The optimal number of clusters can be found by using 
	- the [[StudyNotes/Determining the number of clusters#Elbow Methods\|Determining the number of clusters#Elbow Methods]]
	- Variance-Ratio Criterion (VRC, see [[StudyNotes/Error Metrics#^b9aa3a\|Error Metrics#^b9aa3a]]) 
	- Bayesian Information Criterion (BIC) 
### Measure the separability between clusters: Silhouette Method  
- the score can be increased by applying [[StudyNotes/Dimensionality Reduction\|Dimensionality Reduction]].

# K-modes & K-prototype
## Why K-modes or K-prototype
- K-Means only handles numerical data since it used Euclidian distance
- K-modes is similar to K-Means but designed for binary data
- K-prototype combines K-means with K-modes to handle datasets with both numerical and categorical data 
## How it works
### K-modes
- The process is similar to [[StudyNotes/Centroid-based Clustering#K-Means Clustering\|Centroid-based Clustering#K-Means Clustering#How it works]]
- But it uses **Hamming distance** to count number of mismatched categories
### K-prototype
- The process is similar to [[StudyNotes/Centroid-based Clustering#K-Means Clustering\|Centroid-based Clustering#K-Means Clustering#How it works]]
- But it uses both **Euclidian distance** and **Hamming distance** with weighting factor to balance numeric and categorical contributions

