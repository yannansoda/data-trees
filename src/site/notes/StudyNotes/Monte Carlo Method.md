---
{"topic":"Math","dg-publish":true,"permalink":"/StudyNotes/Monte Carlo Method/","dgPassFrontmatter":true,"noteIcon":""}
---

# Definition
Monte carlo method is a stochastic approximation based on sampling.

# Application
An important application of this method is the intergral calculation.
For $z_1, z_2, ... , z_N \sim p(z|x)$, where $p(z|x)$ is a posterior distribution with latent variable $z$ and observed data $x$, one can calculate the expectation of the posterior via sampling:
$$E _{z|x} [f(z)] = \int p(z|x) f(z) dz
 \approx \frac{1}{N} \sum^N_{i=1} f(z_i)$$
Then a question comes along: How to know the posterior? How to sample from the posterior?

# Sampling Methods
There are several sampling methods.
### Sampling via CDF
Ideally, if one samples $u \sim U(0, 1)$ and locates it on Y-axis of a CDF, a corresponding inverse CDF can be acquired.
This method only works for very simple PDF/CDF forms, e.g. normal distributions.
### Rejection sampling
Rejection sampling means that for the probability of $z^{(i)}$, if it falls in the area under $p(z)$, we accept it; if it falls outside the area of $p(z)$ and inside the area of $Mq(z)$ (where $q(z)$ is a proposal distribution, and $Mq(z_i)$ is always larger than $p(z_i)$), we reject it, i.e. :
$$\forall z_i, Mq(z_i) \geq p(z_i)$$
then we define $\alpha$ as the ratio of acceptance, i.e.
$$\alpha = \frac{p(z_i)}{Mq(z_i)} \ \ (0 \leq \alpha \leq 1)$$
Rejection sampling steps:
1. sample $z_i\sim q(z)$ 
2. sample $u \sim U (0,1)$
3. decision:
	-  if $u \leq \alpha$, accept $z_i$;
	- else, reject $z_i$ 
### Importance sampling
Importance sampling samples from the expectations $E _{z|x} [f(z)]$.
$$E _{z|x} [f(z)]  = \int p(z|x) f(z) dz = \int f(z) \frac{p(z)}{q(z)} q(z) dz
\approx \frac{1}{N} \sum^N_{i=1} f(z_i) \frac{p(z_i)}{q(z_i)}$$
where the $\frac{p(z_i)}{q(z_i)}$ is the weight, and again $q(z)$ is a proposal distribution.
