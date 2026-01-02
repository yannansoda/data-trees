---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Determining the number of clusters/","dgPassFrontmatter":true,"noteIcon":""}
---


## Elbow Methods
![K-Means-1.png|400](/img/user/_assets/images/K-Means-1.png)

**WCSS** is the sum of squared distance between each point and the centroid in a cluster (i.e. cost function):
$$
WCSS = \sum_{Cluster \ j} \ \sum_{Point_i \ in \ Cluster \ j} \ distance(P_i, C_j)^2
$$
![K-Means-2.png|600](/img/user/_assets/images/K-Means-2.png)

## Silhouette score
see [[StudyNotes/Error Metrics#^47335a\|Error Metrics#^47335a]]

### Gap statistic method


