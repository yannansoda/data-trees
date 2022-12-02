---
{"dg-publish":true,"permalink":"/mathcards/goodness-of-fit/"}
---

# Tools to assess goodness of fit
### Maximum Likelihood
see [[Mathcards/Maximum likelihood estimation\|Maximum likelihood estimation]]

### Akaike Information Criterion (AIC)
$$
AIC = - 2ln(L) + 2k
$$
 where $k$ is the number of estimated parameters in the model and $L$ is the maximum value of the likelihood function for the model.
 
 Given a set of candidate models for the data, the preferred model is the one with the minimum AIC value. 
 Thus, AIC rewards goodness of fit (as assessed by the likelihood function), but it also includes a penalty that is an increasing function of the number of estimated parameters. The penalty discourages overfitting, which is desired because increasing the number of parameters in the model almost always improves the goodness of the fit.
 
### BIC
$$
BIC = - 2ln(L) + kln(N)
$$
 where $k$ is the number of estimated parameters in the model, $L$ is the maximum value of the likelihood function for the model, and $N$ is the number of observations.