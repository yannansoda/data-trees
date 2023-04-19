---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Hierarchical Clustering/","dgPassFrontmatter":true,"noteIcon":""}
---


# How it works
1. Make each data point a single-point cluster => that forms N clusters
2. Take the two closest data points and make them one cluster => that forms N-1 clusters
3. Take the two closest data clusters and make them one cluster => that forms N-2 clusters
4. Repeat until there is only one cluster

> - "Closest" means the shortest Euclidian distance
> 
> -  The distance between two clusters can be calculated in different ways
> 	- defined by furtherest/nearest points
> 	- defined by average
> 	- defined by between centroids
	
# Dendrograms
![](/img/user/assets/images/hierarchical-clustering-1.png)
Dendrograms remain the memory of each step in hierarchical clustering.
- You can set a distance threshold and check how many vertical lines are formed below it. The number of lines = the number of clusters
- Optimal number of clusters = the longest vertical line that does not cross the hypothetical horizontal lines 
> *example*:
![](/img/user/assets/images/hierarchical-clustering-2.png)
