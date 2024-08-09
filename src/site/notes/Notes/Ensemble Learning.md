---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Ensemble Learning/","dgPassFrontmatter":true,"noteIcon":""}
---

# What is Ensemble Learning
>[!Quote] The Hundred-Page Machine Learning Book
>Ensemble learning is a learning paradigm that, instead of trying to learn one super-accurate model, focuses on training a large number of low-accuracy models and then combining the predictions given by those weak models to obtain a high-accuracy meta-model.
- It is a machine learning technique that combines multiple models to improve the overall performance of the system. 
- It can be computationally expensive and may require more resources than a single model.

# Types 
### Bagging (Bootstrap Aggregating)
![Pasted image 20230628162612.png|400](/img/user/assets/images/Pasted%20image%2020230628162612.png)
- How it works
	- Bagging is an ensemble learning method in which multiple models are trained **independently** on random subsets of the training data. 
	- The predictions of these models are combined using a simple majority vote (for classification) or an average (for regression) to make the final prediction. 
	- Bagging can improve the accuracy and stability of the model, especially when the individual models are prone to [[Notes/Underfitting vs. Overfitting#Overfitting\|Underfitting vs. Overfitting#Overfitting]].
- Examples
	- [[Notes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]] can be seen as a bagging method for decision trees

### Boosting
![Pasted image 20230628162627.png|400](/img/user/assets/images/Pasted%20image%2020230628162627.png)
- How it works
	- Boosting is an ensemble learning method in which models are trained **sequentially**, with each new model attempting to correct the errors of the previous models. 
	- The final prediction is made by combining the predictions of all the models, weighted by their individual performance. 
	- Boosting can be effective in reducing the bias of the model (i.e. solving [[Notes/Underfitting vs. Overfitting#Underfitting\|Underfitting vs. Overfitting#Underfitting]]), especially when the individual models are simple and have high bias.
- Examples
	- AdaBoost (Adaptive boosting)
	- [[Notes/Gradient boosting\|Gradient boosting]]
		- [[Notes/Gradient boosting#XGBoost (Extreme Gradient Boosting)\|Gradient boosting#XGBoost (Extreme Gradient Boosting)]]
### Stacking
![Pasted image 20230628163006.png|400](/img/user/assets/images/Pasted%20image%2020230628163006.png)
- How it works
	- train base learners from the training data then create a meta-learner that combines the outputs of the base learners to output final predictions
	-  take a majority vote (for classification) or an average (for regression) from all base learners to make the final prediction. 