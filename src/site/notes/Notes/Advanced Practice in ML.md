---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Advanced Practice in ML/","dgPassFrontmatter":true,"noteIcon":""}
---

# Handling data labels
### Label multiplicity
to obtain enough labeled data, companies often use different data sources and annotators. This leads to the problem of label ambiguity: what to do when there are multiple conflicting labels for a data instance.
### Data lineage
= a technique that helps keep track of the origin of each of data samples as well as its labels

# Handling imbalanced dataset
Imbalanced data set makes the normal classification metrics, like accuracy, not work well. There are some solutions:
- Choose other metrics for classification problems, such as precision, recall, F-score
- Data-level methods: Resampling
{ #5cfbc3}

	- Undersampling: down-sampling the larger set 
		- by randomly throwing away some data from that set
	- Oversampling: up-sampling the smaller set  
		- by making multiple copies of the data points in the smaller set (can cause the model to be over-fitting) 
		- by using synthetic data creation such as 
			- synthetic minority oversampling technique (SMOTE)
				- use the existing data in the smaller set to create new data points that look like the existing ones: use the feature vectors of the minority classes to generate syntehtic data points that are between real data points and their k-nearest neighbours
			- adaptive synthetic sampling methods (ADASYN)
- Algorithm-level methods
	- use [[Notes/Ensemble Learning\|Ensemble Learning]] methods, because each model in the ensemble can be trained on a different subset of the data 
	- keep the training data distribution intact but alter the algorithm to make it more robust to class imbalance
	- cost-sensitive learning
	- class-balanced loss
	- focal loss
- Use metric to measure imblance
	- Class imbalance: the imbalance in the number of members between different facet values
	- Difference in proportions of labels (DPL): the imbalance of positive outcomes between different facet values 

# Making feature generalization
Always consider two aspects with regards to generalization:
- feature coverage: the percentage of the samples that has values for this feature in the data -> the fewer values that are missing, the higher the coverage.
- the distribution of feature values

# Model selection
- always consider the **Interpretability** and the **Complexity** of the model.


