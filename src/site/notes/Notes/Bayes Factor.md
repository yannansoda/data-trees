---
{"topic":"Math, Statistics","dg-publish":true,"permalink":"/Notes/Bayes Factor/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is Bayes Factor
- The Bayes factor is a measure used in Bayesian statistics to compare the evidence provided by data for two competing hypotheses. 
- Given two hypotheses $H_0$ (the null hypothesis) and $H_1$ (the alternative hypothesis), the Bayes factor $BF_{10}$​ is calculated as: $$BF_{1,0} = \frac{P(D|H_1)}{P(D|H_0)}$$, where $P(D|H_1)$ is the probability of the data D given that the alternative hypothesis H1​ is true, and $P(D|H_0)$ is the probability of the data D given that the alternative hypothesis H0​ is true.
- It is like a [[Notes/Likelihood ratio test\|Likelihood ratio test]], except we integrate out the parameters, which allows us to compare models of different complexity.

### Interpreting Bayes factors: Jeffreys scale of evidence
- $1 \leq BF_{1,0} < 3$​: anecdotal evidence for H1​
- $3 \leq BF_{1,0} < 10$: Moderate evidence for H1​
- $BF_{1,0} > 10$: Strong evidence for H1​
- $BF_{1,0} > 100$: Very strong evidence for H1​