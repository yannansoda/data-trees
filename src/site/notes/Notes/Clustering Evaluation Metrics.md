---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/Notes/Clustering Evaluation Metrics/","dgPassFrontmatter":true,"noteIcon":""}
---

### Silhouette Method
- It measures how well each data point fits within its cluster compared to other clusters
- It calculates a score for each point based on cohesion (how close it is to points in its own cluster) and separation (how far it is from points in the nearest other cluster)
- **Score range**: −1 to 1
    - **1** = well-clustered     
    - **0** = borderline       
    - **< 0** = likely in the wrong cluster
- applicable to **any clustering algorithm** that produces cluster labels and works with distance metrics
- commonly used to:
    - evaluate overall clustering quality
    - help choose the optimal number of clusters
### Davies–Bouldin Index
- evaluates similarity of clusters based on compactness and separation
- lower is better
### Calinski–Harabasz Index
- ratio of between-cluster to within-cluster dispersion
- higher is better
### Dunn Index
- higher values indicate better clustering by maximizing inter-cluster distance and minimizing intra-cluster distance