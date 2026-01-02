---
{"topic":"Math, Modeling","dg-publish":true,"permalink":"/StudyNotes/Underfitting vs. Overfitting/","dgPassFrontmatter":true,"noteIcon":""}
---

# Underfitting
### Common solutions
- include more features
- try a more complicated model
- for [[StudyNotes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]] and [[StudyNotes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]: 
	- find better network architecture and hyperparameters
	- try longer/better optimization algorithms ([[StudyNotes/Gradient Descent\|Gradient Descent]])

# Overfitting
### Common solutions
- try a simpler model
- collect more data (or training examples) for ML
- [[StudyNotes/Feature selection\|Feature selection]]: select features to include/exclude, when there are multiple features
- [[StudyNotes/Regularization\|Regularization]] => reduce overfitting during estimation
- for [[StudyNotes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]] and [[StudyNotes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]: find better network architecture and hyperparameters


### Estimates of out-of-sample accuracy => estimate the degree of overfitting
- **Cross-validation** => test the model’s predictive accuracy on another sample
{ #ce001d}

	- [[StudyNotes/Cross-Validation\|Cross-Validation]]
- **Information criteria** => construct a theoretical estimate of the relative out-of-sample Kullback-Leibler Divergence ([[StudyNotes/Information theory and Entropy in Neuroscience#^aa57f9\|Information theory and Entropy in Neuroscience#^aa57f9]])
	- [[#Akaike Information Criterion AIC]]
	- Deviance Information Criterion (DIC): a more general version of AIC
	- Widely Applicable Information Criterion (WAIC): even more general than AIC and DIC
	- WAIC PSIS
> BUT! Do not use predictive criteria to choose a causal estimate, because predictive criteria actually prefer confounds in [[StudyNotes/Causal inference#Confounds in causal inference\|Causal inference#Confounds in causal inference]].

