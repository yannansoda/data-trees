---
{"dg-publish":true,"permalink":"/notes/data-preprocessing/"}
---


# Data preprocessing pipeline for ML

1.  taking care of missing data
2.  encoding categorical data with dummy variables
3.  splitting datasets into the training and test sets
4.  [[Data preprocessing pipeline for ML#Feature Scaling\|Data preprocessing pipeline for ML#Feature Scaling]] (optional, but beneficial to gradient descent and calculation speed)
	-   two options
		-   standardization = z-score normalization (universal)
		-   normalization (only apply to normal distribution)
		  $$ \frac{X-X_{min}}{X_{max}-X_{min}} $$
	-   don’t apply feature scaling on dummy variables!

### What is **feature engineering** then?
Feature engineering is the process of selecting, manipulating, and transforming raw data into features that can be used in supervised learning.

### Tips in practice
- missing data: replace NaN by average
- dummy variable trap =  a scenario in which the independent variables are multicollinear:  -> so, always omit one dummy variable!






