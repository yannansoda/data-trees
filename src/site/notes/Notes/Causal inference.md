---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Causal inference/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is Causal inference 
- is prediction of intervention: What if I do this?
- is imputation of missing observations: What if I had done something else?

### Terminology
#### Counterfactuals
- A counterfactual is a hypothetical scenario used to reason about what would have happened if a different action or condition had been present. 
- It’s fundamental in defining causal effects.
- It is different from potential outcomes:
	- potential outcomes framework defines causal effects by comparing what would happen under different treatments or conditions
	- counterfactuals specifically refer to the unobserved outcome that would have occurred under a different scenario than what actually happened

#### Confounder
- A confounder is a variable that influences both the treatment (or exposure) and the outcome, potentially leading to a spurious association if not properly controlled.

#### Causal Effects
- Average Treatment Effect (ATE)
	- = the average difference in outcomes between if everyone was treated with A=1 and if everyone was treated with A=0:
	- formula: 
	$$
	 E(Y^1 - Y^0)
	 $$
	 - note that it is different from conditioning (which compares subpopulation)
	 $$
	 E(Y^1 - Y^0) \neq E(Y|A=1) - E(Y|A=0)
	 $$
- Causal relative risk
	- formula: 	$$
	 E(Y^1 / Y^0)
	 $$
- Conditional Average Treatment Effect (CATE)
	- = the average treatment effect conditional on a set of covariates or specific subgroups
	- formula: $$
	E(Y^1 - Y^0 | V=v)
	$$

#### Fundamental problem of causal inference
- the problem: we only observe one treatment and one outcome for each person

### Causal assumptions
- = the foundational beliefs or conditions necessary to establish valid causal inferences from data
- key causal assumptions
	- stable unit treatment value assumption (SUTVA)
		- no interference (spillover/contagion): the treatment assigned to one individual does not affect the potential outcomes of another individual
		- no hidden variations: there is only one version of each treatment level
	- consistency
		- assumes that the potential outcomes for an individual under a given treatment are exactly what would be observed if that treatment were actually applied
	- ignorability ('no unmeasured confounders')
		- given pre-treatment covariates X, treatment assignment is independent from the potential outcomes
	- positivity
		- assumes that for every combination of confounders, there is a non-zero probability of receiving each treatment level
		- this means that there must be sufficient variation in treatment assignment across all levels of the confounding variables
### Confounds in causal inference
#### The Four Elemental Confounds
{ #b7b0a6}


![4-elemental-confounds.png|300](/img/user/_assets/images/4-elemental-confounds.png)

| Confound type | Description | Take care... |
| --- | --- | --- |
| The Fork | X and Y are associated unless stratified by Z | - |
| The Pipe | X and Y are associated unless stratified by Z | post-treatment bias
| The Collider | X and Y are not associated unless stratified by Z| collider bias |
| The Descendant | X and Y are causally associated through Z | once stratified by A, X and Y are less associated | - |  

### Causal graphs
