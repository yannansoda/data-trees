---
{"dg-publish":true,"permalink":"/Notes/Confusion Matrix/","noteIcon":""}
---


# Confusion Matrix
![confusion-matrix-1.png|300](/img/user/assets/images/confusion-matrix-1.png)
[source](https://towardsdatascience.com/confusion-matrix-for-your-multi-class-machine-learning-model-ff9aa3bf7826)

# Performance measures
## Accuracy 
= the fraction of the total samples that were correctly classified by the classifier

$$(TP+TN)/(TP+TN+FP+FN)$$
## Misclassification Rate/Classification Error
= the fraction of predictions were incorrect

$$(FP+FN)/(TP+TN+FP+FN)$$ or $$(1-Accuracy)$$
## Precision
= the fraction of predictions as a positive class were actually positive
$$TP/(TP+FP)$$
## Sensitivity / True Positive Rate (TPR) / Probability of Detection / Recall
= the fraction of all positive samples were correctly predicted as positive by the classifier
$$TP/(TP+FN)$$
## Specificity / True Negative Rate (TNR)
= the fraction of all negative samples are correctly predicted as negative by the classifier
$$TN/(TN+FP)$$
## F1-score: 
= It combines precision and recall into a single measure. Mathematically it’s the harmonic mean of precision and recall.
$$F1-score = 2 \times \frac{Precision \times Sensitivity}{Precision + Sensitivity}$$


# Cumulative Accuracy Profile (CAP)
*resource*: https://waleblaq.medium.com/the-cap-curves-the-cumulative-accuracy-profile-58a141e01fae
 - CAP is used to visualize the discriminative power of a model. 
 - The CAP of a model represents the cumulative number of positive outcomes along the y-axis versus the corresponding cumulative number of a classifying parameter along the x-axis.
 ## CAP Analysis
We can analyze the cap curve in 2 ways.
 ### Way 1: ratio of the areas under the good model to the area under the ideal curve
 ![](/img/user/assets/images/confusion-matrix-2.png)
 ### Way 2:
![](/img/user/assets/images/confusion-matrix-3.png)
# Receiver Operating Characteristic (ROC)
ROC != CAP, ROC plots the true-positive rate against the false-positive rate.
![](/img/user/assets/images/ROC.png)