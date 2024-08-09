---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Adjusting p-values in Statistical analysis/","dgPassFrontmatter":true,"noteIcon":""}
---

# Why need adjusting p-values
- Adjusting p-values is necessary to account for multiple hypothesis testing, reducing the likelihood of false positive results when conducting numerous statistical comparisons simultaneously

# Methods
| Method                        | Description                                       | When to Use                                                                                                 |
| ----------------------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Bonferroni                    | One-step correction                               | Use when the number of comparisons is small or when strict control of the family-wise error rate is needed. |
| Sidak                         | One-step correction                               | Similar to Bonferroni, but slightly less conservative. Use when controlling the family-wise error rate.     |
| Holm-Sidak                    | Step-down method using Sidak adjustments          | Use when controlling the family-wise error rate with a step-down approach.                                  |
| Holm                          | Step-down method using Bonferroni adjustments     | Use when controlling the family-wise error rate with a step-down approach.                                  |
| Simes-Hochberg                | Step-up method (independent)                      | Use when controlling the false discovery rate (FDR) with independent tests.                                 |
| Hommel                        | Closed method based on Simes tests (non-negative) | Use when controlling the FDR with non-negative dependencies among tests.                                    |
| Benjamini/Hochberg            | Benjamini/Hochberg (non-negative)                 | Use when controlling the FDR and the tests are independent or positively correlated.                        |
| Benjamini/Yekutieli           | Benjamini/Yekutieli (negative)                    | Use when controlling the FDR and the tests are dependent, possibly negatively correlated.                   |
| Two-stage Benjamini/Hochberg  | Two-stage FDR correction (non-negative)           | Use when controlling the FDR with potentially dependent tests, particularly for non-negative dependencies.  |
| Two-stage Benjamini/Yekutieli | Two-stage FDR correction (non-negative)           | Similar to Two-stage Benjamini/Hochberg but offers improved control over the FDR under certain conditions.  |
