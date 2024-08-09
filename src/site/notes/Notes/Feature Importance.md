---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/Notes/Feature Importance/","dgPassFrontmatter":true,"noteIcon":""}
---

### Coefficient-based methods
linear regression, logistic regression)
### Impurity-based methods
- Feature importance is calculated as the decrease in node impurity weighted by the probability of reaching that node.
- Tree-based models have a strong tendency to overestimate the importance of continuous numerical or high cardinality categorical features.

### SHapley Additive exPlanations (SHAP)
>[!Reading]
>https://christophm.github.io/interpretable-ml-book/shap.html

- What is SHAP values:
	- SHAP values have their roots in cooperative game theory, where Shapley values are used to quantify the contribution of each player to the game.
- How does it work
	- It considers all possible combinations of features and measure the change in the model’s prediction when a specific feature is included or excluded.
- Why is it useful:
	- It explains predictions made by black-box machine learning models: given a prediction made by a machine learning model, SHAP values explain the prediction by quantifying the additive importance of each feature to the prediction. 
	- The importance values can be positive or negative.
	- It can be calculated for each individual dataset to explore how features influenced the prediction result for this specific dataset
- Cons?
	- computationally expensive to compute SHAP values for general black-box models; in the case of trees and forests there exists a fast polynomial-time algorithm