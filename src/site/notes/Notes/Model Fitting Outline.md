---
{"dg-publish":true,"permalink":"/notes/model-fitting-outline/"}
---

1. draft & implement model
	- linear/logistic regression: [[Notes/Regression\|Regression]]
	- ...
- 2. estimate parameters of the model
	- optimal parameters minimize the cost function 
		- cost function = averaged loss (+ regularization components) [[Notes/Cost Functions\|Cost Functions]]
		- the minimum of the cost function is found with gradient descent 
		- the loss/cost function can have different forms, e.g. [[Notes/Cost Functions#Loss for logistic regression\|Cost Functions#Loss for logistic regression]]
		- [[Notes/Maximum likelihood estimation\|Maximum likelihood estimation]] is also a form of cost function..?
	- overfitting vs. underfitting <= [[Notes/Bias-Variance Tradeoff\|Bias-Variance Tradeoff]]
		- 3 methods to address [[Notes/Overfitting\|Overfitting]] 
			- increase data size 
			- feature selection: decrease # of variables
			- [[Notes/Regularization\|Regularization]] 
		