---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/Notes/Scaling Law/","dgPassFrontmatter":true,"noteIcon":""}
---


## What is scaling law
Given a compute budget, the rule that helps calculate the optimal model size and dataset size is called the **Chinchilla scaling law**.

- for compute-optimal training, the number of training tokens is approximately 20 times the model size
- the model size and the number of training tokens should be scaled equally: for every doubling of the model size, the number of training tokens should also be doubled
