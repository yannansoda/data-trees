---
{"dg-publish":true,"permalink":"/notes/regression/"}
---

# Linear Regression
### Prerequisites
- linearity 
- homoscedasticity
- multivariate normality
- independence of errors
- lack of multicollinearity
### Terminology
- ML: x = feature, y =  target variable ()
- 
### Multiple Linear Regression
5 methods of building regression models: the choice of predictive variables?
- All-in
- Backward Elimination (fastest)
	1. select a significance level (SL, e.g. SL=0.05)
	2. fit the full model with all possible predictors
	3. consider the predictor with the highest P-vales. If P > SL, go to step 4, otherwise go to FIN
	4. remove the predictor
	5. fit model without this variable
	6. return to step 3
- Forward Selection 
	1. select a significance level (SL, e.g. SL=0.05)
	2. fit all simple regression models. Select the one with the lowest P-value
	3. keep this variable and fit all possible models with one extra predictor added to the one(s) you already have.
	4. consider the predictor with the lowest P-value. If P < SL, go to step 3, otherwise go to FIN and keep the previous model
- Bidirectional Elimination (stepwise regression)
	= combination of Backward Elimination and Forward Selection
	1.  select a significance level to enter and stay in the model (SL, e.g. SL=0.05)
	2. perform the next step of forward selection (new variables must have P < SL_enter to enter)
	3. perform all steps of backward elimination (old variables must have P < SL_enter to stay)
	4. repeat step 2 and 3, until no new variables can enter and no old variables can exit
- Score Comparison: All possible models (time-consuming)
	1. select a criterion of goodness of fit
	2. construct all possible regression models
	3. select the one with the best criterion


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


