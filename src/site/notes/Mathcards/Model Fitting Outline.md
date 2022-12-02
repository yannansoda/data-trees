---
{"dg-publish":true,"permalink":"/mathcards/model-fitting-outline/"}
---

1. draft & implement model
	- linear/logistic regression: [[Mathcards/Regression\|Regression]]
	- ...
- 2. estimate parameters of the model
	- optimal parameters minimize the cost function 
		- cost function = averaged loss (+ regularization components) [[Mathcards/Cost Functions\|Cost Functions]]
		- the minimum of the cost function is found with gradient descent 
		- the loss/cost function can have different forms, e.g. [[Mathcards/Cost Functions#Loss for logistic regression\|Cost Functions#Loss for logistic regression]]
		- [[Mathcards/Maximum likelihood estimation\|Maximum likelihood estimation]] is also a form of cost function..?
	- overfitting vs. underfitting <= [[Mathcards/Bias-Variance Tradeoff\|Bias-Variance Tradeoff]]
		- 3 methods to address [[Mathcards/Overfitting\|overfitting]] 
			- increase data size 
			- feature selection: decrease # of variables
			- [[DataScience/Regularization\|regularization]] 
		