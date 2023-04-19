---
{"dg-publish":true,"permalink":"/Notes/Bias-Variance Tradeoff/","noteIcon":""}
---

Bias-Variance trade-off -> Underfitting vs. [[Notes/Overfitting\|Overfitting]] issues

# Bias & Variance in ML
### Evaluate bias & variance
You can evaluate the bias and variance by checking errors of the train and dev sets. 

| Train set error | Dev set error | type |
| -- | -- | -- |
| low (1%) | high (11%) | high variance |
| high (15%) | high, but near train set error (16%) | high bias |
| high (15%) | high, but much higher than Train set error (30%) | high bias & high variance|
| low (0.5%) |  low (1%) | low bias & low variance |


### Regularization influences bias-variance trade-off
check [[Notes/Cost Functions#Cost function with regularization\|Cost Functions#Cost function with regularization]] and [[Notes/Regularization\|Regularization]]

![bias-variance-1.png|600](/img/user/assets/images/bias-variance-1.png)

![bias-variance-4.png|600](/img/user/assets/images/bias-variance-4.png)



### learning curves
![bias-variance-2.png|300](/img/user/assets/images/bias-variance-2.png)
![bias-variance-3.png|300](/img/user/assets/images/bias-variance-3.png)
increasing training set size can...
- lower cross validation error, if a learning algorithm suffers from high variance
- not help anything, if a learning algorithm suffers from high bias

### How to fix
- High bias
	- try getting additional features
	- try adding polynomial features
	- try decreasing [[Notes/Regularization\|Regularization]] parameter $\lambda$
- High variance
	- get more training examples
	- try smaller sets of features
	- try increasing [[Notes/Regularization\|Regularization]] parameter $\lambda$

# Bias & Variance in Deep Learning
> [!Important] Different from simple ML models, there is rarely trade-off between bias-variance in DL models. You can now reduce bias without hurting variance, and vice versa.

![Pasted image 20230313213430.png|400](/img/user/assets/images/Pasted%20image%2020230313213430.png)