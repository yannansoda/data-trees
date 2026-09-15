---
{"topic":"DataScience, AIxHealth","dg-publish":true,"permalink":"/LearningNotes/Clinical Prediction Models/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"DataScience, AIxHealth"}}
---

>[!abstract] Summary


>[!info] Related Notes
>- 
# Model development 
## Development step by step
> [!Source] Source 
> [Developing clinical prediction models: a step-by-step guide](https://www.bmj.com/content/386/bmj-2023-078276)
>
1. Define aims, create a team, review literature, start writing a protocol
2. Develop a new model, or update an existing one
3. Define the outcome measure
4. Identify candidate predictors and specify measurement methods
5. Collect and examine data
6. Consider sample size
7. Deal with missing data
8. Fit the prediction models
9. Assess the performance of prediction model
	1. Internal validation
	2. Εxternal validation
10. Decide on the final model
11. Perform a decision curve analysis
>[!Tip] Decision curve analysis (DCA)
> DCA measures something called Net Benefit (= weighting the consequences of false positives and false negatives against patient and policy-maker preferences). 
> - It is a method for evaluating whether a prediction model is actually useful for making clinical decisions. 
> - It's useful because for healthcare the cost of a false positive (e.g., an unnecessary, invasive procedure) is usually much different than a false negative (e.g., missing a severe diagnosis).
> - It basically compares predictive models against two universal baseline scenario: take action for all patients vs. take action for no patients.
> 	- Thus, the net benefit is compared between three strategies. For example, the strategies to be compared can be:
> 		- refer a patient for ECG if the model predicted risk exceeds 10%
> 		- refer everyone
> 		- refer no one
12. Assess the predictive ability of individual predictors (optional step)
13. Write up and publish