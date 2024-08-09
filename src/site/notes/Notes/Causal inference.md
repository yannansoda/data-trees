---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Causal inference/","dgPassFrontmatter":true,"noteIcon":""}
---

## What is Causal inference 
- is prediction of intervention: What if I do this?
- is imputation of missing observations: What if I had done something else?
## Confounds in causal inference
### The Four Elemental Confounds
{ #b7b0a6}


![/assets/images/4-elemental-confounds.png|300](/img/user/assets/images/4-elemental-confounds.png)

| Confound type | Description | Take care... |
| --- | --- | --- |
| The Fork | X and Y are associated unless stratified by Z | - |
| The Pipe | X and Y are associated unless stratified by Z | post-treatment bias
| The Collider | X and Y are not associated unless stratified by Z| collider bias |
| The Descendant | X and Y are causally associated through Z | once stratified by A, X and Y are less associated | - |  


