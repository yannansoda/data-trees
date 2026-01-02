---
{"topic":"MachineLearning, DeepLearning, DataScience","dg-publish":true,"permalink":"/StudyNotes/Human-level performance/","dgPassFrontmatter":true,"noteIcon":""}
---

Machine learning systems should achieve human-level performance, and can even surpass human-level performance (online advertising, product recommendations, logistics, etc.)

>[!Careful]
>Which humans do you choose to define human-level performance?


# Why compare to human-level performance?
- Because the workflow of designing and building a machine learning system is more efficient when it mimics human-level performance.
- Because the human-level error as a proxy for Bayes error

# What to do when ML is worse than humans
- get labeled data from humans
- gain insight from manual error analysis: why did a person get this right?
- better analysis of bias/variance
	- if training error is much higher than human-level error -> reduce bias
	- if training error is comparable to human-level error, but test error is higher -> reduce variance

# What if human-level performance is bad too?
- if HLP is << 100%, it may indicate ambiguous labelling instructions or label inconsistency 

