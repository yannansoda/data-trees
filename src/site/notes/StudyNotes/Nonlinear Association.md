---
{"topic":"Statistics","dg-publish":true,"permalink":"/StudyNotes/Nonlinear Association/","dgPassFrontmatter":true,"noteIcon":""}
---

 
## Why we need nonlinear association
[[StudyNotes/Correlation\|Correlation]] cannot reveal nonlinear relation between variables: exponential, logistic, quadric, cubic...

## Which methods can measure nonlinear association
### Distance Correlation
 Distance Correlation is a measure of dependence between two paired random vectors of arbitrary, not necessarily equal, dimension:
 $$ dCor(X, Y) = \frac{dCov(X,Y)}{\sqrt{dVar(X)dVar(Y)}} $$
 - ranging from 0 to 1: 0 = no association
 - symmetric: dCor(X, Y) = dCor(Y, X)
 - comparing to Pearson's correlation ![Pasted image 20240423142103.png](/img/user/_assets/images/Pasted%20image%2020240423142103.png)
### Mutual information
see [[StudyNotes/Information theory and Entropy in Neuroscience#Mutual Information\|Information theory and Entropy in Neuroscience#Mutual Information]]
- cons: no range limit, hard to interpret

