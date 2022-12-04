---
{"dg-publish":true,"permalink":"/notes/feature-scaling/"}
---


# Feature Scaling
= a method used to normalize the range of independent variables or features of data
## Normalization
= min-max scaling / min-max normalization
$$
x' = \frac{x - min(x)}{max(x) - min(x)}
$$

## Standardization 
= subtract mean and divide by standard deviation => afterwards the data follow Normal(0, 1)
$$
x' = \frac{x - \bar x}{ \sigma}
$$
	- computation works better
	- easy to choose sensible priors (then you can detect small slope values like 0.5)
