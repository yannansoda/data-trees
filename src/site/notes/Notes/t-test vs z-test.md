---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/t-test vs z-test/","dgPassFrontmatter":true,"noteIcon":""}
---


Both t-tests and z-tests can be used to test whether a population mean is equal to a particular value or whether the means from two different populations are equal.

- the difference lies in test statistics:
	- z-test statistic follows a normal distribution
	- t-test statistic follows a student t-distribution (which involves estimating population variance)
- how to choose:
    - for small sample size (<30): if population variance is known → z-test, otherwise → t-test
    - for large sample size (>30): z-test works anyway because of central limit theorem
    - for very large sample size (>200): z-test works anyway because the t-distribution will resemble a normal distribution in this case