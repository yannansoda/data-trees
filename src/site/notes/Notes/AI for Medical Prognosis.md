---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/Notes/AI for Medical Prognosis/","dgPassFrontmatter":true,"noteIcon":""}
---



>![Source]
>The contents and notes are from Coursera course "AI for Medical Prognosis".

# What is Medical Prognosis 
- prognosis = Predicting the risk of a future event
    - risk of illness
    - survival probability with illness
- examples
    - use clinical history, physical examinations, labs & imaging, etc. to predict the risk score/survival probability

# Build & Evaluate Risk Models
### Risk model types
- linear risk model
	- risk score = a linear sum of the coefficient x feature
- tree-based model
	- be cautious about missing data
		- identifying missing data types
		    - missing completely at random = missingness not dependent on anything → no bias
		    - missing at random  = missingness dependent only on the available information (for somewhat feature criteria)
		    - missing not at random = missingness dependent on unavailable information
		- use data imputation to handle missing data ([[Notes/Data preprocessing#^594d05\|Data preprocessing#^594d05]])
### Risk model evaluation
- Since the risk score can be any value, it needs to be compared in pairs. In a group of predicted patients, 
{ #d82ca5}

	- concordant pair: if patient A has a higher risk outcome than patient B, and A’s risk score is higher than B’s risk score  
	- risk ties: patient's risk scores are the same  
	- permissible pair: patients’ outcomes are not the same
- Thus:
    - +1 for a permissible pair that is concordant
    - +0.5 for a permissible pair for risk tie
- C-index (max 1, 0.5 for any random constant risk)
    $$ \frac{\#concordant \ pairs + 0.5 \times \#risk \ ties}{\#permissible \ pairs} $$

# Build & Evaluate Survival Model
### What does survival model tell 
- What is the probability of survival past any time t?
- With survival functions: S(t) = Pr(T>t)
    - always decreasing from 1 to 0: longer the t, harder to survive
### Survival data structure
- in survival data, the labels are amounts of time to event
- censoring observations: no observations of events happening in the specified time period:
	- end-of-study censoring (no event)
	- loss-to-follow-up censoring (patients withdraw)
- right censoring = the time to events is only known to exceed a certain value (e.g. 12 months → 12m +)
### Estimate survival 
Let $i$ = 1, ..., $n$ be the cases, and let $T_i$ be the time when $i$ was censored or an event happened. Let $e_i= 1$ if an event was observed for $i$ and 0 otherwise. Then let $X_t = \{i : T_i > t\}$, and let $M_t = \{i : e_i = 1 \text{ or } T_i > t\}$. The estimator will be:  $$
        
        \hat{S}(t) = \frac{|X_t|}{|M_t|} $$
- Kaplan Meier estimate: the probability of survival past t months with censored observations  $$ S(t) = \prod 1- Pr(T=i | T >= i ) = \prod_{t_i \leq t} (1 - \frac{d_i}{n_i}) $$
- $t_i$ are the events observed in the dataset 
- $d_i$ is the number of deaths at time $t_i$
- $n_i$ is the number of people who we know have survived up to time $t_i$.
### Survival model types
- Hazard functions
	- Hazard: what’s a patient’s immediate risk of death if they make it to time t (risk of death if aged t)
        $$ \lambda (t) = \prod Pr(T=t | T >= t ) $$
	- cumulative hazard $$ \Lambda (t) = \int _0
{ #t}
 \lambda(u) du $$
	- individual hazard $$ \lambda_{individual} (t) = \lambda_{0} (t) exp (\sum_i {B_i X_i}) $$ where $\lambda_0(t)$ is a baseline hazard, B_i is coefficient of factor X_i
    
	- relation between survival and hazard: $$ S(t) = exp(- \int _0
{ #t}
 \lambda(u) du) $$
    $$ \lambda(t) = -\frac{S'(t)}{S(t)} $$
- Survival trees
	- Nelson Aalen Estimator: estimate the cumulative hazard of the population
	$$
	H(t) = \sum_{i=0}
{ #t}
 \frac{d_i}{n_i}
	$$
	
	- Mortality score = a single score value of cumulative hazard at the event times
### Survival model evaluation
- as a variation of evaluating prognostic models, with a slightly different definition of a concordant pair, a risk tie, and a permissible pair with survival data
    - here the risk outcome is the time to the event
    - concordant pairs: the patients with worse risk outcome (earlier event) have higher risk scores
    - permissible pairs: patients’ event times are not the same
        ![Pasted image 20231106120739.png|500](/img/user/assets/Pasted%20image%2020231106120739.png)
    - Harrell’s C-Index: same as the C-index formula