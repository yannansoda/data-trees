---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Naive Bayes/","dgPassFrontmatter":true,"noteIcon":""}
---

# How it works
1.  Calculate the posterior of category 1 (C1) given X:
 $$P(C1 | X) = \frac{P(X | C1) P (C1)}{P(X)}$$
 where the marginal likelihood $P(X)$ is determined by the size of the cluster around $X$ (the gray circle below).
 ![](/img/user/assets/images/naive-bayes-1.png)
 2. Calculate the same for other categories (C2, ...) (==by using the same P(X)==)
 4. Compare $P(C1|X)$ with $P(C2|X)$ to classify 
 > thus you can ignore the marginal likelihood P(X) because it is same for all categories.
 
 > - Why "Naïve"
> - Often although it applies and works, the variables are not independent.
 