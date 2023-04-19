---
{"dg-publish":true,"permalink":"/Notes/Non-parametric methods/","noteIcon":""}
---

# Intro
## Parametric vs Non-parametric

- parametric methods: 
	-  a set of fixed parameters
	- assume the distribution is Gaussian and set the significance level
	- the result or outputs generated can be easily affected by outliers
- non-parametric methods:
	- no assumption of parameters
	- no assumption of the distribution
	- the result or outputs generated cannot be easily affected by outliers
	
## Benefits of Non-parametric
- avoid Type I error
- 30% trials would be already enough to show the effects

# Non-parametric methods
| NONPARAMETRIC TEST | PARAMETRIC ALTERNATIVE | DESCRPTION |
| -- | -- | -- |
| 1-sample sign test [[Notes/Paired-data tests#the sign test\|Paired-data tests#the sign test]]| One-sample Z-test, One sample t-test | estimate the median of a population and compare it to a reference value |
| 1-sample Wilcoxon Signed Rank test | One sample Z-test, One sample t-test | same as sign test, but requiring a symmetric distribution|
| Friedman test	| Two-way ANOVA | by ranks: tests whether n treatments in randomized block designs have identical effects | 
| Kruskal-Wallis test | One-way ANOVA | tests whether > 2 independent samples are drawn from the same distribution |
| Mann-Whitney test |Independent samples t-test | compare differences between two independent groups, or Wilcoxon rank sum test |
| Mood’s Median test | One-way ANOVA | Use this test instead of the sign test when you have two independent samples |
{ #e259ea}



## Permutation test
- not assuming any distribution
- test whether the obeserved data differ from the randomly shuffled data
- any statistical tests can be applied to the shuffled data