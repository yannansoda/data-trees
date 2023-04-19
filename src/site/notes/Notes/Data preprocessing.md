---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/Notes/Data preprocessing/","dgPassFrontmatter":true,"noteIcon":""}
---


# Data preprocessing pipeline for ML

1.taking care of **missing data** (e.g. replace NaN by average)

2.**categorical encoding** = converting categorical columns to numerical columns 

- two approaches
	- Label encoding
	- One-hot encoding

> [!Choices of approaches]
> - Label encoding is suitable when:
> 	- the categorical feature is ordinal
> 	- the number of categories is quite large (high cardinality)
> - One-hot encoding is suitable when:
> 	- the categorical feature is not ordinal 
> 	- the number of categories is quite small (low cardinality)
 	
> [!Challenges of One-Hot Encoding: Dummy Variable Trap]
>  a scenario in which the independent variables are multicollinear:  -> so, always omit one dummy variable!

3.**splitting datasets** into the training and test sets

4.**feature scaling**
- a method used to normalize the range of independent variables or features of data
- optional, but beneficial to gradient descent and calculation speed
- don’t apply feature scaling on dummy variables!
- two options
	- standardization 
		- = z-score normalization (universal) = subtract mean and divide by standard deviation => afterwards the data follow Normal(0, 1)
		- easy to choose sensible priors (then you can detect small slope values like 0.5)
		- computation works better

$$
x' = \frac{x - \bar x}{ \sigma}
$$
	 .  - normalization 
			- = min-max scaling / min-max normalization
			- only apply to normal distribution

$$
x' = \frac{x - min(x)}{max(x) - min(x)}
$$

### What is **feature engineering** then?
Feature engineering is the process of selecting, manipulating, and transforming raw data into features that can be used in supervised learning.


