---
{"dg-publish":true,"permalink":"/Notes/K-Means Clustering/","noteIcon":""}
---


# How it works
1. Choose the number K of clusters
2. Select at random K points, the centroids (not necessarily from your dataset)
3. Assign each data point to the closest centroid => that forms K clusters
4. Compute and place the new centroid of each cluster
5. Reassign each data point to the new closest centroid
8. Repeat until your model is ready (i.e. cost function reaches minimum

> Actually, in K-means, the cost never increases.

# Traps during use!!!
### Random Initialisation trap
- = the random centroids at the start may lead to inappropriate clustering
- solution: 
	- use more than more one random initialisation (50 - 1000)
	- K-Means++ (already implemented in python/R)
### Choosing the right number of clusters
The optimal number of clusters can be found by using the **Elbow Method**.
![](/img/user/assets/images/K-Means-1.png)
WCSS is the sum of squared distance between each point and the centroid in a cluster (i.e. cost function):
$$
WCSS = \sum_{Cluster \ j} \ \sum_{Point_i \ in \ Cluster \ j} \ distance(P_i, C_j)^2
$$
![](/img/user/assets/images/K-Means-2.png)
