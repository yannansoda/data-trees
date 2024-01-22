---
{"topic":"Math, Modeling","dg-publish":true,"permalink":"/Notes/Underfitting vs. Overfitting/","dgPassFrontmatter":true,"noteIcon":""}
---

# Underfitting
### Common solutions
- include more features
- try a more complicated model
- for [[Notes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]] and [[Notes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]: 
	- find better network architecture and hyperparameters
	- try longer/better optimization algorithms ([[Notes/Gradient Descent\|Gradient Descent]])

# Overfitting
### Common solutions
- try a simpler model
- collect more data (or training examples) for ML
- [[Notes/Feature selection\|Feature selection]]: select features to include/exclude, when there are multiple features
- [[Notes/Regularization\|Regularization]] => reduce overfitting during estimation
- for [[Notes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]] and [[Notes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]: find better network architecture and hyperparameters


### Estimates of out-of-sample accuracy => estimate the degree of overfitting
- **Cross-validation** => test the model’s predictive accuracy on another sample
{ #ce001d}

	- [[Notes/Cross-Validation\|Cross-Validation]]
- **Information criteria** => construct a theoretical estimate of the relative out-of-sample Kullback-Leibler Divergence ([[Notes/Infomation theory and Entropy#^aa57f9\|Infomation theory and Entropy#^aa57f9]])
	- [[Notes/Underfitting vs. Overfitting#Akaike Information Criterion AIC\|#Akaike Information Criterion AIC]]
	- Deviance Information Criterion (DIC): a more general version of AIC
	- Widely Applicable Information Criterion (WAIC): even more general than AIC and DIC
	- WAIC PSIS
> BUT! Do not use predictive criteria to choose a causal estimate, because predictive criteria actually prefer confounds in [[Confounds in Causal Models#^b7b0a6\|Confounds in Causal Models#^b7b0a6]].

