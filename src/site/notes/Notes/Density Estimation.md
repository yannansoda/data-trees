---
{"topic":"Math","dg-publish":true,"permalink":"/Notes/Density Estimation/","dgPassFrontmatter":true,"noteIcon":""}
---

# What is density estimation?
- Density estimation=reconstructing the probability density function of a random variable, _X_, given a sample of random variates $X_1, X_2,..., Xn.$
# Categories
- **Parametric density estimation**
	- assumes X follows some distribution that may be characterized by some parameters
	- parameter estimates can be plugged in the corresponding density function formula for X
- **Non-parametric density estimation**
	- makes less rigid assumptions about the distribution of X
	- estimates the shape of the density function directly from the empirical data
# Non-parametric density estimation
## Histograms
- produces density estimates that follow a discrete distribution
- the choice of binning can have a disproportionate effect on the resulting visualization
## Kernel Density Estimators (KDE)
### How KDE works
- First, you need to know how a **naive density estimator** works as a "moving histogram": it extends the traditional histogram by estimating density at a point based on observations within a centered interval
- Then, KDE just generalizes the **naive density estimator** by replacing the uniform density function with an arbitrary density function, **the [[Notes/Kernel Function\|Kernel Function]]**.
### Parameters of KDE
- **kernel**
	- specifies the shape of the distribution placed at each point
	- kernel selection: [[Notes/Kernel Function#Types of Kernels\|Kernel Function#Types of Kernels]]
- **kernel bandwidth**
	- controls the size of the kernel at each point
	- it acts as a smoothing parameter, controlling the tradeoff between bias and variance in the result
	- a large bandwidth leads to a very smooth (i.e. high-bias) density distribution
	- a small bandwidth leads to an unsmooth (i.e. high-variance) density distribution
	- bandwidth selection methods: 
		- unbiased cross-validation
		- Sheather-Jones methods 