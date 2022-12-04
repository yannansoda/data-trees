---
{"dg-publish":true,"permalink":"/notes/regularization/"}
---



# Regularization
#TODO check https://bjlkeng.github.io/posts/probabilistic-interpretation-of-regularization/

### What is regularization
- Regularization = the process of adding information in order to solve an ill-posed problem or to prevent overfitting.
- Regularization lets you keep all of your features, but they just prevents the features from having an overly large effect, which is what sometimes can cause overfitting.

### Cost function with regularization
When you choose regularization, a regularization term will be added to the cost function.  
See [[Notes/Cost Functions#Cost function with regularization\|Cost Functions#Cost function with regularization]].

### Regularized regression
- Ridge Regression
- Lasso
- Elastic Net

### Regularization in Bayesian framework
- A regularizing prior is a "skeptical" prior, which means it slows down the rate of the model in learning from the data.
- Multilevel models can be regarded as adaptive regularization, where the model itself tries to learn how skeptical it should be.
- It is a Bayesian method. It is the same device that non-Bayesian methods refer to as “penalized likelihood.”