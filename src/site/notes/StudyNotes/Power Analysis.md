---
{"topic":"Statistics","dg-publish":true,"permalink":"/StudyNotes/Power Analysis/","dgPassFrontmatter":true,"noteIcon":""}
---

### Definition
Power analysis can be used to calculate the minimum sample size required so that one can be reasonably likely to detect an effect of a given size. 

Power values range from 0 to 1, and a common power value is 0.8

### Example
for two groups A and B:

$$d = \frac{\mu_a - \mu_b}{SD_ab}$$
where d is the effect size, $\mu$ is the mean of each group, and SD is the pooled estimated SD.
Then you can Google with the combination of effect size, power, and desired significance threshold.


Rule of thumb
$$
n = \frac{2\sigma^2 (z_{\alpha/2} + z_{\beta})^2}{\delta^2}
$$
where
- $\sigma^2$ : variance
- $\alpha$: significance level, Type I error (false positive)
- $\beta$: Type II error (false negative)
- $\delta$: difference between the two groups
Therefore, more samples are needed when 
- large variance in historical tests and data
- high confidence level (smaller alpha and beta)
- small difference between groups