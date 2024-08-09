---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/Notes/Propensity Score Matching/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is PSM
- Propensity score = the probability of each participant being in the group A or B
	- e.g. group A is with treatment, group B is without treatment
- Propensity Score Matching (PSM) is a quasi-experimental method the researcher uses statistical techniques to construct an artificial control group by matching each treated unit with a non-treated unit of similar characteristics
- Using these matches, the researcher can estimate the impact of an intervention

### How does it work
It is basically a logistic regression using the control covariates
- calculate the propensity score of 
	- the disease/treatment group based on the control variables
	- the control group based on the control variables
- match individuals from the control group to those in the disease group with similar scores using [[Notes/K-Nearest Neighbor\|K-Nearest Neighbor]]

### Why PSM is useful
- it can help create matched groups
- it can help avoid confounds: [[Notes/Causal inference#Confounds in causal inference\|Causal inference#Confounds in causal inference]]
- it can provide robust solution for estimating causal effects in observational studies
