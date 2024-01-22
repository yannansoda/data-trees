---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Connectivity-based Clustering/","dgPassFrontmatter":true,"noteIcon":""}
---

> Connectivity-based methods group data points together based on the proximity between the clusters.

# Calculate proximity between the clusters using linkage criterion
- **Single linkage**
	- Distance between closest points of clusters; minimum distance between clusters
	- Good for detecting arbitrarily shaped clusters but cannot detect overlapping clusters. It is efficient to compute but is not robust to noisy data
- **Complete / Maximum linkage**
	- Distance between furthest points of clusters; maximum distance between clusters. 
	- Good for detecting overlapping clusters but cannot detect arbitrarily shaped clusters
- **Average linkage**
	- Average of all distances across two clusters
- **Centroid linkage**
	- Distance between centers of two clusters
- **Ward linkage**
	- Ward linkage is the default linkage criterion
	- Sum of squared distance from each data point to the centroid of the cluster they are assigned to.
	- This results in cluster merging that gives the smallest increase in total variance within all clusters. 
# ## Hierarchical Clustering
## How it works
1. Make each data point a single-point cluster => that forms N clusters
2. Take the two closest data points and make them one cluster => that forms N-1 clusters
3. Take the two closest data clusters and make them one cluster => that forms N-2 clusters
4. Repeat until there is only one cluster

> - "Closest" is defined using the linkage criterion mentioned above.
	
# Dendrograms
![/assets/images/hierarchical-clustering-1.png|600](/img/user/assets/images/hierarchical-clustering-1.png)
Dendrograms remain the memory of each step in hierarchical clustering.
- You can set a distance threshold and check how many vertical lines are formed below it. The number of lines = the number of clusters
- Optimal number of clusters = the longest vertical line that does not cross the hypothetical horizontal lines 
> *example*:
![](/img/user/assets/images/hierarchical-clustering-2.png)
