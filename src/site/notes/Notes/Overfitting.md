---
{"dg-publish":true,"permalink":"/Notes/Overfitting/","noteIcon":""}
---


### Common tools to address overfitting: 
- Collect more data (or training examples) for ML
- Feature selection: select features to include/exclude, when there are multiple features
- [[Notes/Regularization\|Regularization]] => reduce overfitting during estimation

### Estimates of out-of-sample accuracy => estimate the degree of overfitting
- **Cross-validation** => test the model’s predictive accuracy on another sample
	- It divides the sample in a number of chunks, called “folds.” The model is asked to predict each fold, after training on all the others.
	- It is extremely common to use the maximum number of folds, resulting in leaving out one unique observation in each fold. This is called **leave-one-out cross-validation.**
	- An improved cross-validation: **Pareto-smoothed importance sampling cross-validation (PSIS)**
- **Information criteria** => construct a theoretical estimate of the relative out-of-sample Kullback-Leibler Divergence ([[Notes/Infomation theory and Entropy#^aa57f9\|Infomation theory and Entropy#^aa57f9]])
	- [[Notes/Overfitting#Akaike Information Criterion AIC\|#Akaike Information Criterion AIC]]
	- Deviance Information Criterion (DIC): a more general version of AIC
	- Widely Applicable Information Criterion (WAIC): even more general than AIC and DIC
	- WAIC PSIS
> BUT! Do not use predictive criteria to choose a causal estimate, because predictive criteria actually prefer confounds in [[Confounds in Causal Models#^b7b0a6\|Confounds in Causal Models#^b7b0a6]].

