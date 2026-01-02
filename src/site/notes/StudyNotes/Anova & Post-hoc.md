---
{"topic":"Statistics","dg-publish":true,"permalink":"/StudyNotes/Anova & Post-hoc/","dgPassFrontmatter":true,"noteIcon":""}
---


## ANOVA
## Basics
- ANOVA is a special case of [[StudyNotes/Linear mixed models\|Linear mixed models]]: it assumes the data are idd and continuous, while generalized linear mixed models do not.
- [[StudyNotes/F-distribution & F-Test\|F-distribution & F-Test]]
### Choosing ANOVA types
- How many independent variables do you have?
	n variables => n-way ANONA
- Whether you are replicating (i.e. duplicating) your tests with multiple groups?
	Yes, e.g. two groups of students from two colleges taking two tests => ANOVA with replication
- Whether you are comparing within subject?
	Yes,  e.g. changes in mean scores of same item over three or more time points=> Repeated Measures ANOVA (it is one-way here)

### Prerequisite
- the group sizes are same
- the population is normal
	<= can be tested using [[StudyNotes/Normality Tests\|Normality Tests]]
- the groups have equal variance
	<= can be tested by **Levene's [[StudyNotes/Test for Equality of Variances\|Test for Equality of Variances]]**
- for a repeated-measures ANOVA, you have to be careful about the sphericity
	- Sphericity is an important assumption of a repeated-measures ANOVA. It is the condition where the variances of the differences between all possible pairs of within-subject conditions (i.e., levels of the independent variable) are equal. 
	- It can be tested by the **Mauchly's sphericity test (Mauchly's W)**, which is a statistical test used to validate a repeated measures ANOVA.

## Post-hoc
A post hoc test is used only **after** we find a statistically significant result and need to determine where our differences truly came from. 
It usually follows an ANOVA test.
#### Tukey test