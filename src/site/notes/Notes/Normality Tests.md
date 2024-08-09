---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Normality Tests/","dgPassFrontmatter":true,"noteIcon":""}
---

### Types of Normality tests
| Test                     | Null hypothesis | When to use                                                     | Features                                                                                                        |
| ------------------------ | --------------- | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Shapiro–Wilk test (best) | normality       | small to moderate sample sizes (up to around 2000 observations) | known for its power and reliability in detecting deviations from normality                                      |
| Anderson–Darling         | normality       | larger sample sizes                                             | sensitive to deviations (tails)                                                                                 |
| Kolmogorov-Smirnov       | normality       | any sample size                                                 | sensitive to differences in both location and shape between the sample distribution and the normal distribution |
| Lilliefors               | normality       | when the mean and variance of the population are unknown        | A modification of the Kolmogorov-Smirnov test that provides estimates of parameters from the sample data.       |
