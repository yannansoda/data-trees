---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Paired-data tests/","dgPassFrontmatter":true,"noteIcon":""}
---

### paired t-test (2 groups)

Paired t-test analysis is performed as follow:

1.  Calculate the difference (d) between each pair of value
2.  Compute the mean (m) and the standard deviation (s) of d
3.  Compare the average difference to 0. If there is any significant difference between the two pairs of samples, then the mean of d (m) is expected to be far from 0.

Paired t-test can be used only when the difference d is **normally distributed**. This can be checked using [Shapiro-Wilk test**](http://www.sthda.com/english/wiki/normality-test-in-r).

### the sign test (2 groups)

The sign test is a statistical method to test for consistent differences between pairs of observations, such as the weight of subjects before and after treatment. Given pairs of observations (such as weight pre- and post-treatment) for each subject, the sign test determines **if one member of the pair (such as pre-treatment) tends to be greater than (or less than) the other member of the pair (such as post-treatment)**.

The paired observations may be designated x and y. For comparisons of paired observations (x,y), the sign test is most useful if comparisons can only be expressed as x > y, x = y, or x < y. 

If, instead, the observations can be expressed as numeric quantities (x = 7, y = 18), or as ranks (rank of x = 1st, rank of y = 8th), then the paired t-test\[1\] or the Wilcoxon signed-rank test\[2\] will usually have greater power than the sign test to detect consistent differences.

	Relationship to other tests
	- Paired t-test: it does not require the difference within each pair to be normally distributed, but paired t-test does.
	- Wilcoxon signed-rank test: Wilcoxon signed-rank test requires rank and have greater power.

