---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Ensemble Learning/","dgPassFrontmatter":true,"noteIcon":""}
---

# What is Ensemble Learning
- It is a machine learning technique that combines multiple models to improve the overall performance of the system. 
- It can be computationally expensive and may require more resources than a single model.

# Types 
### Bagging (Bootstrap Aggregating)
- How it works
	- Bagging is an ensemble learning method in which multiple models are trained independently on random subsets of the training data. 
	- The predictions of these models are combined using a simple majority vote (for classification) or an average (for regression) to make the final prediction. 
	- Bagging can improve the accuracy and stability of the model, especially when the individual models are prone to overfitting.
- Examples
	- Random Forest can be seen as a bagging method for decision trees

### Boosting
- How it works
	- Boosting is an ensemble learning method in which models are trained sequentially, with each new model attempting to correct the errors of the previous models. 
	- The final prediction is made by combining the predictions of all the models, weighted by their individual performance. 
	- Boosting can be effective in reducing the bias of the model, especially when the individual models are simple and have high bias.
- Examples
	- AdaBoost
	- [[Notes/Gradient boosting\|Gradient boosting]]
		- [[Notes/Gradient boosting#XGBoost (Extreme Gradient Boosting)\|Gradient boosting#XGBoost (Extreme Gradient Boosting)]]