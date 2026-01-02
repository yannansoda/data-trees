---
{"topic":"Math, Modeling","dg-publish":true,"permalink":"/StudyNotes/Gaussian Process/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Resource]
>https://youtu.be/UBDgSHPxVME?feature=shared


>[!Quote]
Any model that is linear in its parameters with a Gaussian distribution over the parameters is a Gaussian process. 

>[!Quote]
 If we observe a set of points, then we can condition on these points and infer a distribution over what the value of the function might look like at any other input.- [D2L](https://d2l.ai/chapter_gaussian-processes/index.html)

To put it straightforward: Gaussian process predicts the distribution rather than the value of y for an x, and the important thing here is that the distribution of y depends on x.

# How does GP work (layman version)
1. specify a prior distribution over reasonable types of functions
2. condition on data, average the values of every possible sample function from the posterior

# Kernel:  How is GP controlled
- Kernel controls which functions are likely to be sampled
- kernel = a covariance function which measures the similarity of two inputs $x$ and $x'$, written as $$K (x, x'| \tau)$$where $\tau$ is a vector of hyperparameter used to tune it
### Examples
- 1 dimensional radial basis function (RBF) $$k_{RBF} \{x, x') = Cov(f(x), f(x'))= a^2 \ exp( - \frac{1}{2l^2} ||x-x'||^2)$$
	- with RBF, GP will sample functions with nearby y's for x's deemed similar by the kernel
	- hyperparameters
		- length-scale parameter $l$: larger -> slower rate of variation of the function (larger interval between x)
		- amplitude parameter $a$: larger -> larger vertical scale over which functions vary
- periodic kernel $$k_{} \{x, x') = exp( - \frac{2}{l^2} sin
{ #2}
 (\frac{\pi}{p}|x-x'|))$$
### Combining kernels
- addition
- multiplication 

# Types of uncertainty
- epistemic uncertainty

# Math behind GP
- A Gaussian process represents a distribution over functions by specifying a multivariate Gaussian distribution over all possible function values