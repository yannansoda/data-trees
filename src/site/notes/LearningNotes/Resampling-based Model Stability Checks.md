---
{"topic":"DataScience, MachineLearning, Modeling","dg-publish":true,"permalink":"/LearningNotes/Resampling-based Model Stability Checks/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"DataScience, MachineLearning, Modeling"}}
---

# Resampling-based Stability Checks

= use repeated data resampling to check whether model results are stable under changes in the training data.

## Common resampling schemes
- **Repeated train/test splits**: repeatedly create random train/test splits, fit the model, and compare results across splits
- **Cross-validation folds**: fit models across CV folds and check whether results are consistent
- **Bootstrap samples**: repeatedly sample with replacement and estimate variation in the result
- **Subsampling**: repeatedly sample without replacement, often using only part of the training data

## What can be checked

| What you track across resamples | What you are checking |
| -- | -- |
| model performance, e.g. AUC/RMSE | **model performance robustness** |
| predictions for the same samples | **prediction stability** |
| selected variables/features | **feature selection stability** |
| coefficient sizes/signs | **parameter stability** |
| feature importance rankings | **interpretability stability** |

## Typical workflow
1. Resample the data many times
2. Fit the model each time
3. Record the quantity of interest
4. Summarize its variation across resamples
5. Check whether the conclusion is stable enough to trust



