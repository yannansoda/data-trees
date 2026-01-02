---
{"topic":"Math","dg-publish":true,"permalink":"/StudyNotes/Conjugate distribution/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is conjugate prior
In Bayesian statistics, if the posterior $p(\theta | y)$ and the prior $p(\theta)$ follow a same type of distribution (e.g. both follow the normal distribution), we will say this prior is conjugate for the likelihood $p(y|\theta)$.
>[!Note]
 You can always say that **a  prior is a conjugate for a likelihood; but a posterior never has conjugates.**

### Why need conjugate prior
If the prior is conjugate for the likelihood, we can compute the posterior in closed form.

| likelihood              | conjugate prior                                                                 |     |
| ----------------------- | ------------------------------------------------------------------------------- | --- |
| Bernoulli, binominal    | Beta                                                                            |     |
| Categorical distrbution | Dirichlet distribution (a multivariate generalization of the Beta distribution) |     |
| Poisson, exponential    | Gamma                                                                           |     |
| normal with known var   | normal                                                                          |     |
| normal with known mean  | inverse-Gamma                                                                   |     |