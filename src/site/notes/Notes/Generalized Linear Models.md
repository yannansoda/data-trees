---
{"dg-publish":true,"permalink":"/notes/generalized-linear-models/"}
---

- GLMs = generalized linear models
- GLMS are a class of models that map high-dimensional inputs into a scalar output.
- The expected value is ==some function== of an additive combination of parameters.
- It combines a linear filter + a nonlinear function + noise
- linear regression, logistic regression, and Poisson regression, are all just special cases of GLMs.
	- linear: 
$$ Y_i \sim Normal (\mu_i, \sigma) $$$$ \mu_i = \alpha + \beta_X X_i + \beta_Z Z_i $$
	- logistic: 
$$ Y_i \sim Bernoulli (p_i) $$
$$ logit(p_i) = \alpha + \beta_X X_i + \beta_Z Z_i $$
	- Poisson:
	$$ Y_i \sim Poisson (\lambda) $$$$\lambda = \exp(\alpha + \beta_X X_i + \beta_Z Z_i)$$