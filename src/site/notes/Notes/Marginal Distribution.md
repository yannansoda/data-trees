---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Marginal Distribution/","dgPassFrontmatter":true,"noteIcon":""}
---

# Marginal Distribution
### Definition
The marginal distribution of a subset of a collection of random variables is the probability distribution of the variables contained in the subset.
- For discrete variables x and y:
$$
p(x) = \sum_y p(x, y) = \sum_y p(x|y) p(y)
$$
- For continuous variables x and y:
$$
p(x) = \int_y p(x, y) dy = \int_y p(x|y)p(y)dy
$$
### Application of marginalisation
- discrete form: 
$$
p(x|z) = \sum_y p(x, y|z) = \sum_y p(x|y, z) p(y|z)
$$
- continuous form:
$$
p(x|z) = \int_y p(x|y, z)p(y|z)dy
$$
when x and z are independent:
$$
p(x|z) = \int_y p(x|y)p(y|z)dy
$$

# Predictive Distribution
For parameter $\theta$ and observed data $Y$, both prior $p(\theta)$ and posterior $p(\theta | Y)$ distributions focus on the parameter $\theta$. If you want to predictive new data $\hat y$, you need predictive distribution of $\hat y$ using prior information (Prior Predictive Distribution) or observed data (Posterior Predictive Distribution). 
### Prior Predictive Distribution
with marginalisation of prior
$$
p(y) = \int p(y |\theta)p(\theta)d\theta
$$
### Posterior Predictive Distribution
$$
p(\hat y|Y) = \int p(\hat y | \theta, Y) p(\theta |Y) d\theta
$$
if we assume new data $\hat y$ are independent from $Y$:
$$
p(\hat y|Y) = \int p(\hat y | \theta) p(\theta |Y) d\theta
$$
