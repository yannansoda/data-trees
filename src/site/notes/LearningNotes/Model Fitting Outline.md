---
{"topic":"Math, Modeling","dg-publish":true,"permalink":"/LearningNotes/Model Fitting Outline/","dgPassFrontmatter":true,"noteIcon":""}
---

### 1. draft & implement model
- linear/logistic regression: [[LearningNotes/Regression\|Regression]]
- ...


### 2. estimate parameters of the model
- optimal parameters minimize the cost function 
	- cost function = averaged loss (+ regularization components) [[LearningNotes/Cost Functions\|Cost Functions]]
	- the minimum of the cost function is found with gradient descent 
	- the loss/cost function can have different forms, e.g. [[LearningNotes/Cost Functions#Loss for logistic regression\|Cost Functions#Loss for logistic regression]]
	- [[LearningNotes/Maximum likelihood estimation\|Maximum likelihood estimation]] is also a form of cost function..?
- overfitting vs. underfitting <= [[LearningNotes/Bias-Variance Tradeoff\|Bias-Variance Tradeoff]]

### 3. methods to address [[LearningNotes/Underfitting vs. Overfitting\|Underfitting vs. Overfitting]] 
- increase data size 
- feature selection: decrease # of variables
- [[LearningNotes/Regularization\|Regularization]] 
	