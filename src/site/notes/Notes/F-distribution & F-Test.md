---
{"dg-publish":true,"permalink":"/Notes/F-distribution & F-Test/","noteIcon":""}
---

# F-distribution (F-ratio)
$$
X = \frac{S_1/d_1}{S_2/d_2}
$$

where $S_1$ and $S_2$ are independent random variables with [[Notes/Chi-square Test#Chi-square distribution\|Chi-square Test#Chi-square distribution]] with respective degrees of freedom $d_1$ and $d_2$. 

# F-test
Any test that uses the F-distribution can be called a "F-test".
Generally, F-test can compare two variances.
## Overall F-test for Regression Analysis
An overall F-test assesses how well the set of independent variables, as a group, explains the variation in the dependent variable. That is, the F-statistic is used to test whether at least one of the independent variables explains a significant portion of the variation of the dependent variable.
F = MSM  / MSE = (explained variance) / (unexplained variance)
where MSM stands for Mean Squares for Model, and MSE stands for Mean Squares for Error.
$$
F = \frac{\frac{\sum (\hat y_i - \bar y)^2}{k}}{\frac{\sum (\hat y_i -y_i)^2}{n-k-1}}
$$
where k is the number of independent variables , and n is the number of observations.
> - source as regression, degrees of freedom =  k
> - source as error, degrees of freedom = n-k-1
> - total, degrees of freedom = n−1

## F-test for ANOVA
F = MSB / MSE 
where MSB stands for Sum of Squares between the groups, and MSE stands for The Error Mean Sum of Squares
$$
F = \frac{\frac{SS_{between}}{m-1}}{\frac{SS_{within}}{n-m}}
$$
where m is the number of groups, and n is the number of observations (data points). 
> - for n total data points, degrees of freedom =  n−1
> - for m compared groups, degrees of freedom = m−1 
> - for n total data points collected and m groups being compared, degrees of freedom = n−m

# F-test for compare two models
The F-test can be used to compare two competing regression models in their ability to “explain” the variance in the dependent variable.
$$
F = \frac{\frac{RSS_1 - RSS_2}{k_2 - k_1}}{\frac{RSS_2}{n - k_2}}
$$
where RSS stands for residual sum of squares of fitted model 1 or 2, and k stands for degree of freedoms. 