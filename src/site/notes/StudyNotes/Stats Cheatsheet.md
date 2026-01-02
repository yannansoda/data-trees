---
{"topic":"Statistics","dg-publish":true,"permalink":"/StudyNotes/Stats Cheatsheet/","dgPassFrontmatter":true,"noteIcon":""}
---


>[!Purpose] A cheatsheet for the stats terms we all know without telling but cannot describe it precisely when being asked.
>[Source](https://towardsdatascience.com/22-statistics-questions-to-prepare-for-data-science-interviews-d5651a8b3c56)

- **P-value**
	- the probability of observing the data if the null hypothesis is true
- **confidence level in hypothesis testing**
	- the probability of not rejecting the null hypothesis when the null hypothesis is True
- **confidence interval**
	- an interval estimation of a parameter obtained through statistical inference
- **statistical power**
	- the probability of rejecting the null hypothesis when the null hypothesis is False
- **Central Limit Theorem (CLM)**
	- no matter what is the population’s original distribution, when taking random samples from the population, the distribution of the means or sums from the random samples approaches a normal distribution, with mean equals to the population mean, as the random sample size gets larger:
	- ![Pasted image 20230602153018.png|400](/img/user/_assets/images/Pasted%20image%2020230602153018.png)
- **Law of Large Numbers**
	- number of trials gets large enough, the average result of the trials will become closer to the expected value
- **confounding variable**
	-  a variable that is correlated with both the dependent variable and the independent variable
- **Five key assumptions of linear regression**
	- Linear relationship
	- Multivariate normality: All the variables together should be multivariate normal.
	- No or little multicollinearity: Multicollinearity happens when the independent variables are highly correlated with each other.
	- No auto-correlation
	- Homoscedasticity: same variance = residuals are equal across regression line