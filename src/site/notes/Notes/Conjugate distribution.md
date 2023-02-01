---
{"dg-publish":true,"permalink":"/notes/conjugate-distribution/"}
---


In Bayesian statistics, if the posterior $p(\theta | y)$ and the prior $p(\theta)$ follow a same type of distribution (e.g. both follow the normal distribution), we will say this prior is conjugate for the likelihood $p(y|\theta)$.
>[!Note]
 You can always say that **a  prior is a conjugate for a likelihood; but a posterior never has conjugates.**


| likelihood | conjugate prior | 
| -- | -- |
| Bernoulli, binominal | Beta |
| Poisson, exponential | Gamma | 
| normal with known var | normal |
| normal with known mean | inverse-Gamma|