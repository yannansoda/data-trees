---
{"topic":"Data Science, MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Distribution-based Clustering/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Source] 
>https://towardsdatascience.com/6-types-of-clustering-methods-an-overview-7522dba026ca

> Distribution-based methods group data points together based on their likelihood of belonging to the same probability distribution.


# Examples
- Gaussian mixture model (GMM)
# Gaussian mixture model (GMM)
## How it works
- GMM assumes that every data point is generated from multiple Gaussian distributions with unknown parameters
- performs iterative Expectation Maximization (EM) steps to fit the data points
	- In the Expectation (E) step: data points are assigned to clusters that assume randomly selected Gaussian parameters
	- In the Maximization (M) step: the parameters of the Gaussian distribution are updated to best fit the data points in the cluster
- It allows each example to be a member of several clusters with different membership score 