---
{"topic":"Math, Modeling","dg-publish":true,"permalink":"/StudyNotes/Regression/","dgPassFrontmatter":true,"noteIcon":""}
---

# Linear Regression
### Prerequisites
- linearity 
- homoscedasticity
- multivariate normality
- independence of errors
- lack of multicollinearity

# Principal component regression
> [Source](https://towardsdatascience.com/principal-component-regression-clearly-explained-and-implemented-608471530a2f)
1. apply PCA ([[StudyNotes/Dimensionality Reduction#PCA vs. LDA\|Dimensionality Reduction#PCA vs. LDA]]) to generate principal components from the predictor variables, with the number of principal components matching the number of original features p
2. keep the first k principal components that explain most of the variance (where k < p), where k is determined by cross-validation
3. fit a linear regression model on these k principal components
# Partial least squares (PLS) regression
- when dependent variables are multiple and can be correlated
- similar to [[StudyNotes/Regression#Principal component regression\|Regression#Principal component regression]] but run PCA and regression in one go (apply PCA on both independent and dependent variables)
- 
# Logistic Regression

A logistic regression model:
$$
logit(p) = ln(\frac{p}{1-p}) = \beta_0 + \beta_1X_1 + \beta_2X_2 + \beta_kX_k
$$
 
 The odd ratio is the ratio of two groups' odds of some outcome:
$$
odd \ ratio = \frac{p_a}{1-p_a} /\frac{p_b}{1-p_b}
$$ 
Odd ratios can be derived from logistic coefficients:
$$
\beta_x = logit(p_a) - logit(p_b) = ln(odd \ ratio)
$$


# Multivariate regression
> [!INFO]
> Multivariate regression != Multiple regression



# R-Squared: coefficient of determination
$$
R^2 = 1 - \frac{sum\  squared\ regression\  (SSR)}{total\  sum\  of\  squares (SST)}
= 1 - \frac{\sum{(y_i - \hat{y_i})^2}}{\sum{(y_i - \overline{y})^2}}
$$

- It assesses the goodness of fit of regression models.
- It represents the proportion of the variance for a dependent variable that's explained by an independent variable or variables in a regression model.
- It can be negative in extreme cases, but usually it is in $[0, 1]$.

You can regard the R-Squared as how much the total variance of y is captured by the model (rather than errors), i.e.
$$
var(y) = var(X\hat \beta) + var(e)
$$

$$
R^2 = \frac{var(X \hat\beta)}{var(y)}
$$

so it measures the goodness of fit, but it does not validate the model.

## Adjusted R-Squared
Adjusted R-squared is a **modified version of R-squared** that has been adjusted for the number of predictors in the model.

$$
Adj\ R^2 = 1 - (1 - R^2) \frac{n-1}{n-p-1} 
$$
where $p$ is the number of regressors/predictors, $n$ is the sample size.
> Why you need adjusted R-squared?
It is important, because adding independent variables will make the R-squared never decrease, then you cannot tell whether the increase of R-squared is due to the goodness of fit or more variables.
It includes the penalising factor that penalises you for adding independent variables that don't help your model.





