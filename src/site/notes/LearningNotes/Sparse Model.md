---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/LearningNotes/Sparse Model/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"DataScience, MachineLearning"}}
---

# Sparse vs. Non-sparse Models
### Sparse Model
= a model where many feature coefficients/weights are exactly zero or effectively unused
- example
	- Lasso / L1-regularized models
	- ElasticNet
- easy to define "selected features" = features with non-zero coefficients
### Non-sparse model
= a model that can use many or all features at once
- examples
	- ridge regression
	- [[LearningNotes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
	- [[LearningNotes/Gradient Boosting\|Gradient Boosting]]
	- [[LearningNotes/Artificial Neural Networks\|Artificial Neural Networks]]