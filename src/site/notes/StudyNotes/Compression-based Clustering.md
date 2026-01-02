---
{"topic":"Data Science, MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Compression-based Clustering/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Source] 
>https://towardsdatascience.com/6-types-of-clustering-methods-an-overview-7522dba026ca


> Compression-based methods transform data points to an embedding and subsequently perform clustering on the lower-dimension data.

# Examples
- Spectral clustering
	- transforms the affinity matrix between data points to a low-dimension embedding before performing clustering (such as [[StudyNotes/Centroid-based Clustering#K-Means Clustering\|Centroid-based Clustering#K-Means Clustering]])
- BIRCH 
	- BIRCH performs lossy compression of data points to a set of Clustering Features nodes (CF Nodes) that forms the Clustering Feature Tree (CFT). New data points are ‘shuffled’ into the tree until it reaches a leaf and store information regarding the subcluster within the node.
	- Information regarding the final cluster centroids is read off the leaf and other clustering algorithms (such as [[StudyNotes/Connectivity-based Clustering#Hierarchical Clustering\|Connectivity-based Clustering#Hierarchical Clustering]]) can be subsequently performed.

