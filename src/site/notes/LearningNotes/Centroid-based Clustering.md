---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/LearningNotes/Centroid-based Clustering/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"DataScience, MachineLearning"}}
---

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
- **K-Means**: fast baseline for numerical data
- **K-modes**: categorical data
- **K-prototype**: mixed numerical and categorical data
- **K-Medoids**: data with outliers or custom distance metrics
- **Mean Shift**: when you do not want to predefine K
- **Fuzzy Clustering** (soft K-means; data points can be part of multiple clusters): when clusters can overlap and soft membership is useful
## Comparison of centroid-based methods
| Method           | Best for                           | Center type         | Distance / similarity            | Require choosing K | Main weakness                                       |
| ---------------- | ---------------------------------- | ------------------- | -------------------------------- | ------------------ | --------------------------------------------------- |
| K-Means          | numerical data                     | mean point          | Euclidian distance               | Yes                | sensitive to outliers                               |
| K-Medoids        | numerical or custom-distance data  | real data point     | many distance metrics            | Yes                | slower than K-Means                                 |
| K-modes          | categorical data                   | mode                | Hamming / matching dissimilarity | Yes                | only for categorical data                           |
| K-prototype      | mixed numerical + categorical data | mean + mode         | Euclidian + categorical mismatch | Yes                | needs weighting between feature types               |
| Mean Shift       | unknown number of clusters         | dense region / mode | distance + bandwidth             | No                 | sensitive to bandwidth and slower on large datasets |
| Fuzzy Clustering | overlapping clusters               | fuzzy centroid      | usually Euclidian distance       | Yes                | harder to interpret than hard clustering            |

## General tips during use
### Choose the right number of clusters
- K-Means, K-Medoids, K-modes, K-prototype, and Fuzzy Clustering usually require choosing K
- Mean Shift does not require predefined K, but it depends strongly on the bandwidth parameter
- The optimal number of clusters can be found by using 
	- the [[LearningNotes/Determining the number of clusters#Elbow Methods\|Determining the number of clusters#Elbow Methods]]
	- Variance-Ratio Criterion (VRC, see [[LearningNotes/Error Metrics#^b9aa3a\|Error Metrics#^b9aa3a]]) 
	- Bayesian Information Criterion (BIC) 
### Measure the separability between clusters: Silhouette Method  
- Silhouette score can be used for many clustering methods, not only K-Means ([[LearningNotes/Clustering Evaluation Metrics#Silhouette Method\|Clustering Evaluation Metrics#Silhouette Method]])
- Make sure the distance metric matches the data type
- the score can be increased by applying [[LearningNotes/Dimensionality Reduction\|Dimensionality Reduction]]
### Watch out for scale and high dimensionality
- Distance-based clustering methods are sensitive to feature scale
- Standardise numerical features before clustering when features use different units
- Clustering algorithms can have a difficult time accurately clustering data of high dimensionality (ie. too many features)

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
>**K-Means Clustering vs. KNN ([[LearningNotes/K-Nearest Neighbor\|K-Nearest Neighbor]])**
>
>| K-means clustering | KNN |
>| -- | -- |
>| k = number of clusters | k = number of nearest neighbors |
>| unsupervised learning | supervised learning |
>| clustering | regression & classification |
>| to optimize, use elbow method | to optimize, use cross validation & confusion matrix |
>
## K-Means-specific tips
### Random Initialisation trap
- = the random centroids at the start may lead to inappropriate clustering
- solution: 
	- use more than more one random initialisation (50 - 1000)
	- K-Means++ (already implemented in python/R)

# K-modes & K-prototype
## Why K-modes or K-prototype
- K-Means only handles numerical data since it used Euclidian distance
- K-modes is similar to K-Means but designed for binary data
- K-prototype combines K-means with K-modes to handle datasets with both numerical and categorical data 
## How it works
### K-modes
- The process is similar to [[LearningNotes/Centroid-based Clustering#K-Means Clustering\|Centroid-based Clustering#K-Means Clustering#How it works]]
- But it uses **Hamming distance** to count number of mismatched categories
### K-prototype
- The process is similar to [[LearningNotes/Centroid-based Clustering#K-Means Clustering\|Centroid-based Clustering#K-Means Clustering#How it works]]
- But it uses both **Euclidian distance** and **Hamming distance** with weighting factor to balance numeric and categorical contributions

# K-Medoids
## Why K-Medoids
- K-Medoids is similar to [[LearningNotes/Centroid-based Clustering#K-Means Clustering\|K-Means]], but the cluster center is an **actual data point** instead of the mean of all points
- The selected center point is called a **medoid**
- It is more robust to **outliers** because extreme values cannot pull the center as strongly as in K-Means
- It can work with different distance measures, not only Euclidian distance
## How it works
1. Choose the number K of clusters
2. Select K data points as the initial medoids
3. Assign each data point to the closest medoid
4. For each cluster, try replacing the current medoid with another point in the same cluster
5. Keep the replacement if it reduces the total distance between points and their medoid
6. Repeat until the medoids no longer change

> [!Note]
> The objective is to minimize the total distance between each data point and the medoid of its cluster.
>
> Common algorithm: **PAM** (Partitioning Around Medoids)

# Mean Shift
## Why Mean Shift
- Mean Shift does not require choosing K in advance
- It finds dense regions of data points and treats them as clusters
- It is useful when clusters have irregular shapes

## How it works
1. Choose a bandwidth, which controls the search radius
2. For each point, look at nearby points within the bandwidth
3. Shift the point toward the mean of nearby points
4. Repeat until points converge to dense regions
5. Points that converge to the same region are grouped into the same cluster

> [!Note]
> The bandwidth parameter is very important: too small can create too many clusters, too large can merge different clusters.

# Fuzzy Clustering
## Why Fuzzy Clustering
- Fuzzy Clustering allows one data point to belong to multiple clusters
- Instead of hard labels, each point gets a degree of membership for each cluster
- This is useful when cluster boundaries are not clear
## How it works
1. Choose the number K of clusters
2. Initialize K cluster centers
3. Assign each data point a membership score for each cluster
4. Update cluster centers based on the weighted membership scores
5. Repeat until the cluster centers or membership scores stop changing

> [!Example]
> A customer can be 70% in one segment and 30% in another segment instead of belonging fully to only one group.
