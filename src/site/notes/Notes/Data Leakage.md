---
{"topic":"DataScience","dg-publish":true,"permalink":"/Notes/Data Leakage/","dgPassFrontmatter":true,"noteIcon":""}
---

Data leakage refers to the phenomenon when a form of the label “leaks” into the set of features used for making predictions, and this same information is not available during inference.

### Common Causes for Data Leakage

- Splitting time-correlated data randomly instead of by time
- Scaling before splitting
- Filling in missing data with statistics from the test split
- Poor handling of data duplication before splitting
- Group leakage: A group of examples have strongly correlated labels but are divided into different splits.
- Leakage from data generation process