---
{"topic":"Math","dg-publish":true,"permalink":"/StudyNotes/Metropolis-Hastings Algorithm/","dgPassFrontmatter":true,"noteIcon":""}
---

# What it is
Metropolis-Hastings Algorithm is a general framework which includes as special cases the very first and simpler MCMC [[StudyNotes/Markov chain Monte Carlo Algorithm\|Markov chain Monte Carlo Algorithm]].

# How it works
Consider an arbitrary posterior $p(z)$ and its transition matrix $Q(z \rightarrow z*)$, it cannot always satisfy the detailed balance. If we want to achieve the detailed balance, we should add an acceptance ration $\alpha$, to make the equation correct:
$$p(z) Q(z \rightarrow z^*) \alpha (z, z^*) = p(z^*) Q(z^* \rightarrow z) \alpha (z^*, z)$$
in which one can derive $\alpha$:
$$\alpha (z, z^*) = min (1, \frac{p(z^*) Q(z|z^*)}{p(z), Q(z^*|z)})$$

This is how Metropolis Hastings work:
1. sample $z^* \sim Q(z|z_{i-1})$
2. sample $u \sim U(0, 1)$
3. $\alpha= min (1, \frac{p(z^*) Q(z|z^*)}{p(z), Q(z^*|z)})$
4. decision:
	- if $u \leq \alpha$, accept $z_i = z^*$
	- else, reject $z^*$ and accept $z_i = z_{i-1}$

# Gibbs Sampling
- Gibbs sampling is a special type of Metropolis Hastings sampling. 
- It is an approach to constructing a Markov chain where the probability of the next sample is calculated as the conditional probability given the prior sample.

