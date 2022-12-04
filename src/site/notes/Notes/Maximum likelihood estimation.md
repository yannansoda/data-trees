---
{"dg-publish":true,"permalink":"/notes/maximum-likelihood-estimation/"}
---

# Definition
Maximum likelihood estimation (MLE) is a popular mechanism which is used to estimate the model parameters of a regression model.
In other words, it always first compute the probability("how likely") of a specific data point given a distribution/model, and then seeks for the distribution/model parameters that can maximize the total probabilities of all data points.

> Actually, what is likelihood?
A likelihood function is numerically equal to a conditional probability, but is always a function of the variable after the “|” sign.

# Implementation
I put MLE applications into two categories:
- Easy and intuitive: to estimate the parameters of a distribution

	The key steps are:
		1. formulate PDF of the distribution $P(x_i|\theta)$ 
				e.g. 
				$$ P(x_i|\theta) = \mathcal{N}(x_i,\mu,\sigma) = \frac{1}{\sqrt {2 \pi }\sigma} e^{ - \frac{(x-\mu)^2}{2\sigma ^2}}$$
		2. compute the product of the likelihood of all data points $L(\theta)$
			$$L(\theta)=L(\mu, \sigma) = P(X|\mu,\sigma)=\prod_i^n \mathcal{N}(x_i,\mu,\sigma)$$
- More analytic processes: to estimate the parameters of a model
	
	The key steps are:
		1. formulate the conditional probability $P(y_i|x_i, theta)$
			$$P(y_i|x_i, theta) = f(x_i) $$ 
		2.  compute the product of the likelihood of all y values $L(\theta)$
			$$L(\theta) = P(Y|X, \theta) = \prod_i^n P(y_i|x_i, theta)$$
			
			
# Examples
## Distributions
### Normal distribution
1. formulate PDF of the distribution $P(x_i| \theta)$ 
$$ P(x_i|\theta) = \mathcal{N}(x_i,\mu,\sigma) = \frac{1}{\sqrt {2 \pi }\sigma} e^{ - \frac{(x-\mu)^2}{2\sigma ^2}}$$
2. compute the product of the likelihood of all data points $L(\theta)$
$$L(\theta)=L(\mu, \sigma) = P(X|\mu,\sigma)=\prod_i^n \mathcal{N}(x_i,\mu,\sigma)$$
### Binomial distribution
1. formulate PDF of the distribution $P(x_i| \theta)$ 
$$p_i = b(i; n, p) = \tbinom{n}{i} p^i (1-p) ^{n-i}$$
2. compute the product of the likelihood of all data points $L(\theta)$
$$L(\theta)=L(p) = P(X|p)=\prod_i^n \tbinom{n}{i} p^i (1-p) ^{n-i}$$
## Regressions
### Linear regression 
1. formulate the conditional probability $P(y_i|x_i, theta)$
for a linear regression, we have:
$$\hat y = f(x) = \theta x + \eta$$
e.g., if the noise idd. a normal distribution: $\eta \sim \mathcal{N}(0, \sigma^2)$
then the y idd. also a normal distribution: $\eta \sim \mathcal{N}(\theta x, \sigma^2)$

$$P(y_i|x_i, theta)= \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{1}{2\sigma^2}(y_i-\theta x_i)^2}$$
2.  compute the product of the likelihood of all y values $L(\theta)$
$$L(\theta) = P(Y|X, \theta) = \prod_i^n \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{1}{2\sigma^2}(y_i-\theta x_i)^2}$$

### Logistic regression (here using categorical data)
1. formulate the conditional probability $P(y_i|x_i, theta)$
for a logitstic function representing categorical data ("A" or "B"), we have probability of "A":
$$\hat y = f(x) = \frac{1}{1 + e^{-b(x+c)}}$$
$$P(y_i = category\ A|x_i, theta) = \hat y_i$$
$$P(y_i = category\ B|x_i, theta) = 1 - \hat y_i$$
2. compute the product of the likelihood of all y values $L(\theta)$
$$L(\theta) = P(Y|X, theta) = \prod_i^n \hat y^{y_i} (1 - \hat y) ^ {1-y_i}$$

