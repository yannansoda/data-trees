---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/T-test & so on/","dgPassFrontmatter":true,"noteIcon":""}
---

# Standard t-test
$$ t = \frac{{\bar{X}_1 - \bar{X}_2}}{{\sqrt{\frac{{s_1^2}}{{n_1}} + \frac{{s_2^2}}{{n_2}}}}} $$, where $\bar X$ are means, $s$ are variance, and $n$ are sample sizes. 

# t-test variations

### [[Notes/Paired-data Tests#paired t-test (2 groups)\|Paired-data Tests#paired t-test (2 groups)]]
### Weighted t-test
- = a variation of the standard t-test that takes into account the different variances or sample sizes of the groups being compared: $$ T = \frac{{\bar{X}_1 - \bar{X}_2}}{{\sqrt{\frac{{w_1 s_1^2}}{{n_1}} + \frac{{w_2 s_2^2}}{{n_2}}}}} $$, where $w1_​$ and $w_2$​ are the weights assigned to the variances or sample sizes of the two groups.
- how to decide weights?
	- equal weights
	- inverse variance weights
	- inverse sample size weights
	- custom weights based on knowledge 

# t-test vs. z-test
Both t-tests and z-tests can be used to test whether a population mean is equal to a particular value or whether the means from two different populations are equal.

- the difference lies in test statistics:
	- z-test statistic follows a normal distribution
	- t-test statistic follows a student t-distribution (which involves estimating population variance)
- Which to choose:
    - for small sample size (<30): if population variance is known → z-test, otherwise → t-test
    - for large sample size (>30): z-test works anyway because of central limit theorem
    - for very large sample size (>200): z-test works anyway because the t-distribution will resemble a normal distribution in this case
# t-test vs. Cohen's d

### What is Cohen's d
- a measure of effect size (i.e. the magnitude of the difference) used in statistics to quantify the difference between two group means in terms of standard deviation units. $$d = \frac{\bar x_1 - \bar x_2}{s_{pooled}}$$, where $$s_{pooled} = \sqrt{\frac{(n_1 - 1) s_1^2 + (n_2 - 1)s_2^2} {n_1 + n_2 -2}}$$and $s_1$ and $s_2$ are standard deviations. 
- provides a standardized measure of the effect size: typically, Cohen's d values of 0.2, 0.5, and 0.8 are considered small, medium, and large effect sizes
### Which to choose - you can use both!
- The t-test and Cohen's d are complementary statistical measures used to assess and interpret differences between group means, with the t-test focusing on statistical significance and Cohen's d focusing on effect size.
- While the t-test tells you whether the difference between the means is statistically significant, Cohen's d tells you how large or small that difference is in practical terms.