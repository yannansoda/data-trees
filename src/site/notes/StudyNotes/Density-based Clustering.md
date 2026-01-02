---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Density-based Clustering/","dgPassFrontmatter":true,"noteIcon":""}
---

> Density-based methods group data points together based on density instead of distance.
# How does it work

1. define two hyperparameters: 
	- a distance parameter $\epsilon$ = the maximum distance 
	- a quantity parameter $n$ = the minimum number of examples to put in a cluster
2. Pick an example $x$ from your dataset at random and assign it to cluster 1, then count how many examples have the distance from $x$ less than or equal to $\epsilon$. 
	- If this quantity is greater than or equal to $n$, then put all these $\epsilon$-neighbors to the same cluster 1.
	- Examine each member of cluster 1 and find their respective $\epsilon$-neighbors. If some member of cluster 1 has $n$ or more  $\epsilon$-neighbors, expand cluster 1 by adding those  $\epsilon$-neighbors to the cluster. 
3. Continue expanding cluster 1 until there are no more examples to put in it. 
	- Pick from the dataset another example not belonging to any cluster and put it to cluster 2. You continue like this until all examples either belong to some cluster or are marked as outliers. An outlier is an example whose ϵ\epsilon-neighborhood contains less than nn examples.”
 - It uses a parameter called the minimum cluster size (MinClusterSize) in addition to ε and MinPts.


# Examples 
- DBSCAN (Density-Based Spatial Clustering of Applications with Noise)
- HDBSCAN (Hierarchical Density-Based Spatial Clustering of Applications with Noise)
	- is just an extension of DBSCAN that addresses some of its limitations and builds upon the concept of density-based clustering by introducing a hierarchical approach.
- OPTICS (Ordering Points To Identify the Clustering Structure)



