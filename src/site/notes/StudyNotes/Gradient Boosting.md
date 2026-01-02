---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Gradient Boosting/","dgPassFrontmatter":true,"noteIcon":""}
---

# What is gradient boosting
Gradient boosting is an [[StudyNotes/Ensemble Learning\|Ensemble Learning]] algorithm that combines several weak models, typically decision trees, to create a more accurate and robust model.

### How it works

1.  Initialize the model with a simple model or a constant value that best fits the data.
    
2.  Train a weak model, such as a decision tree, on the training data.
    
3.  Use the weak model to make predictions on the training data.
    
4.  Compute the residuals, or the difference between the predicted values and the actual values, for each training example.
    
5.  **Train another weak model on the residuals from the previous model**.
    
6.  Combine the predictions from the previous weak model and the new weak model to get an updated prediction.
    
7.  Repeat steps 4 to 6 until a stopping criteria is met, such as a maximum number of iterations or a minimum improvement in the loss function.
    
8.  Use the final model to make predictions on new data.
    
>[!Important] Why it is called "gradient boosting"?
>- because it uses a **gradient descent** procedure to minimize the loss when adding new learners to the ensemble.
>- The key idea behind gradient boosting is that **each new weak model is trained to fit the residuals of the previous model**, which allows the model to focus on the most challenging examples.

# Gradient-boosted Trees
= when the weak learner is Classification and Regression [[StudyNotes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]] in gradient boosting
### How it works ![Pasted image 20230709123115.png|600](/img/user/_assets/images/Pasted%20image%2020230709123115.png)
### Hyperparameters
- number of trees
- max depth of trees
- learning rate
- subsample size (for randomly sampling training data)
### Pros & Cons
#### Pros
- can outperform random forest in accuracy
- no data preprocessing is reuqires
- can handle missing data
#### Cons
- computationally expensive (often requires > 1000 trees)
- sacrifices interpretability for accuracy - less interpretative in nature

# XGBoost (Extreme Gradient Boosting) 
- XGBoost is a gradient boosting method that uses  [[StudyNotes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]] as base learners. It is the most popular implementation of gradient boosting.
>[!XGBoost vs. Random forest]
>They are both [[StudyNotes/Ensemble Learning\|Ensemble Learning]] models based on decision tree model. But XGBoost is a [[StudyNotes/Ensemble Learning#Boosting\|Ensemble Learning#Boosting]] model, whereas Random forest is [[StudyNotes/Ensemble Learning#Bagging (Bootstrap Aggregating)\|Ensemble Learning#Bagging (Bootstrap Aggregating)]] model. 

### Features
- Algorithm enhancements
	- XGBoost is a more regularized form of Gradient Boosting. XGBoost uses advanced [[StudyNotes/Regularization\|Regularization]] (L1 & L2), which improves model generalization capabilities. 
	- Efficient handling of missing sata
	- Built-in cross-validation capability (at each iteration)
- System optimization
	- XGBoost delivers high performance as compared to normal Gradient Boosting. Its training is very fast and can be parallelized across clusters.
	- Tree pruning: [[StudyNotes/Decision Tree & Random Forest#^4c01d0\|Decision Tree & Random Forest#^4c01d0]]

# LightGBM (light gradient-boosting machine)
#TODO 
- a decision tree-based framework that combines gradient boosting and ensemble methods to tackle complex problems