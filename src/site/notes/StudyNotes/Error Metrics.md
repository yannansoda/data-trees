---
{"topic":"Math, MachineLearning, DataScience","dg-publish":true,"permalink":"/StudyNotes/Error Metrics/","dgPassFrontmatter":true,"noteIcon":""}
---


# Regression Metrics
- Mean Absolute Error (MAE)
	- measures the absolute difference between the predicted and actual values.
	- Be careful about MAE. Compared to MSE, it does not penalize large errors. But if your loss ([[StudyNotes/Cost Functions\|Cost Functions]]) is just proportional to the size of error, then maybe MAE is better.
- Mean Squared Error (MSE)
	- measures the squared difference between the predicted and actual values.
- Root Mean Squared Error (RMSE)
	- the square root of the MSE, which provides a measure of the average magnitude of the error.
- R-squared (R^2): 
	- measures the proportion of variance in the target variable that is explained by the model.
	- [[StudyNotes/Regression#R-Squared coefficient of determination\|Regression#R-Squared coefficient of determination]]

# Classification Metrics
>[!Source]
>See [[StudyNotes/Confusion Matrix#Performance measures\|Confusion Matrix#Performance measures]]
- Accuracy
	- measures the proportion of correct predictions out of total predictions.
- Precision
	- measures the proportion of true positives (correctly predicted positives) out of all predicted positives.
- Recall (Sensitivity) 
	- measures the proportion of true positives out of all actual positives.
- F1 score
	- a weighted average of precision and recall that balances both measures.
- ROC curve
	- [[StudyNotes/Confusion Matrix#Receiver Operating Characteristic (ROC)\|Confusion Matrix#Receiver Operating Characteristic (ROC)]]
	- ROC characteristics: only works for binary classification
	- ROC AUC: area under ROC curve, works for multiclass

# Time Series Metrics
- MAE
- MSE
- Mean Absolute Percentage Error (MAPE): measures the percentage difference between the predicted and actual values.
- Symmetric Mean Absolute Percentage Error (SMAPE): similar to MAPE, but takes the average of the percentage difference between the predicted and actual values and the percentage difference between the actual and predicted values.
- Mean Absolute Scaled Error (MASE): measures the relative accuracy of forecasts compared to a naive forecast based on the historical data.

# Clustering Metrics
>[!Source] Source: [Evaluation Metrics for Clustering Algorithms](https://towardsdatascience.com/7-evaluation-metrics-for-clustering-algorithms-bdc537ff54d2)

> General evaluation criteria: a good clustering algorithm should have small within-cluster variance and large between-cluster variance.
### Extrinsic Measures: requires ground truth labels
- Rand Index
	- measures the similarity between the cluster assignments by making pair-wise comparisons
	- Rand Index  = # pair-wise correct predictions / # number of all possible pairs
	- a higher score signifies higher similarity
	- Adjusted Rand Index: adjusts for chance by discounting a chance normalization term -> range from -1 to 1, random (uniform) label assignments have scores as 0
- Mutual Information
	- measures the agreement between the cluster assignments
- V-measure
	- measures the correctness (homogeneity and completeness) of the cluster assignments using conditional entropy analysis\
	- range from 0 to 1
- Fowlkes-Mallows Scores
	- measure the correctness of the cluster assignments using pairwise precision and recall

### Intrinsic Measures: not requires ground truth labels
- Silhouette score/coefficient
{ #47335a}

	- measures the between-cluster distance against within-cluster distance
	- range from -1 to 1: 
		- A score of 1 denotes the best, meaning that the data point i is very compact within the cluster to which it belongs and far away from the other clusters
		- Values near 0 denote overlapping clusters
		- mean silhouette over 0.6 is considered a "good" clustering solution
	- tend to be higher for convex clusters
- Calinski-Harabasz Index/Variance Ratio Criterion
{ #b9aa3a}

	- measures the between-cluster dispersion against within-cluster dispersion
	- hard to interpret
- Davies-Bouldin Index
	- measures the size of clusters against the average distance between clusters
	- a lower score signifies better-defined clusters
	- tends to be higher for density-based clustering
### Prediction strength
- How does it work
	1. Split the dataset into training ($X_{tr}$) and test ($X_{te}$) sets
	2. Run the clustering algorithm on both sets using a certain value of $k$ (the number of clusters)
	3. Create a co-membership matrix $D[C(X_{tr}, k), X_{te}]$ of size n_test x n_test, where n_test is the number of observations in the test set and $C(X_{tr}, k)$ is the clustering algorithm (e.g. k-means) fitted to the training set.
	4. Set the ii’-th element of the co-membership matrix to 1 if elements i and i’ of the test set fall into the same cluster, set it to 0 otherwise.
	5. Intuitively, this method measures how well the training set centroids predict co-memberships in the test set. For each pair of test observations that are assigned to the same test cluster (a value of 1 in the co-membership matrix), we determine whether they are also assigned to the same cluster based on the training set centroids.
	6.  The prediction strength of the clustering C(., k) is formally defined as:$$ps(k) = min_{1 \leq j \leq k} \frac{1}{n_{kj}(n_{kj} - 1)} \sum_{i \not{=} i' \in A_{kj}} D[C(X_{tr}, k), X_{te}]_{ii'}$$
	7. For each of the test clusters, we calculate the proportion of observation pairs in that cluster that are also assigned to the same cluster using the training set centroids. The prediction strength is the minimum of this quantity over the k test clusters.
- 0.8–0.9 as a good value for the threshold
- how to implement: see this [article](https://towardsdatascience.com/prediction-strength-a-simple-yet-relatively-unknown-way-to-evaluate-clustering-2e5eaf56643?gi=fcb1b63715a4)


