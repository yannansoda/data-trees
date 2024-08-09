---
{"topic":"Math","dg-publish":true,"permalink":"/Notes/Covariance & Correlation/","dgPassFrontmatter":true,"noteIcon":""}
---


### Variance & Covariance
- Variance measures the variation of a single random variable:
	$$
	\sigma _x^2 = \frac{1}{n-1} \sum^n_{i=1} (x_i - x_\mu)^2
  	$$
- Covariance measures how much two random variables vary together:
	$$
	\sigma (x, y) = \frac{1}{n-1} \sum^n_{i=1} (x_i - x_\mu)(y_i - y_\mu)
	$$
### Covariance Matrix
The diagonal entries of the covariance matrix are the variances and the other entries are the covariances:

$$
Cov(x, y) = \left(\begin{array}{cc} 
\sigma(x, x) & \sigma(x, y)\\
\sigma(y, x) & \sigma(y, y)
\end{array}\right)
$$

where 
1. $\sigma (x, x)$ and $\sigma (y, y)$ are simply same as $\sigma _x^2$ and $\sigma _y^2$, respectively.
2. $\sigma(x, y) = \sigma(y, x)$
	which derives:
$$
C = \frac{1}{n-1} \sum^{n}_{i=1}{(X_i-\bar{X})(X_i-\bar{X})^T}
$$

### Correlation
$$
Corr(x, y)
= \frac{Cov(x, y)}{\sqrt{\sigma _x^2 \sigma _y^2}}
= \frac{Cov(x, y)}{\sigma _x\sigma _y}
$$

[[Notes/Correlation\|Correlation]]

### Covariance vs. Correlation Coefficient
Both of them measure the linear relationship between two variables.
![Pasted image 20231016155016.png](/img/user/assets/images/Pasted%20image%2020231016155016.png)

----
### Reference
- An intuitive example of covariance matrix: https://www.youtube.com/watch?v=152tSYtiQbw&ab_channel=ritvikmath
- Data science example: https://datascienceplus.com/understanding-the-covariance-matrix/
- Example covariance and correlation between two random variables: https://www.youtube.com/watch/KDw3hC2YNFc



