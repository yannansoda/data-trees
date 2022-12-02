---
{"dg-publish":true,"permalink":"/ml/anomaly-detection/"}
---

1. fit distribution model $p(x)$ on training set and predict
$y = 1$ if $p(x) < \epsilon$ (anomaly)
$y = 0$ if $p(x) >= \epsilon$ (normal)
2. evaluate the algorithm using
	- true positive, false positive...
	- precision/recall
	- F1-score: [[ML/Confusion Matrix#F1-score\|Confusion Matrix#F1-score]]

# Anomaly detection vs. supervised learning
Why bother using anomaly detection rather than supervised learning if your examples already have labels?
- Anomaly detection is more proper than supervised learning, when:
	- very small number of anomalous examples
	- future anomalies may look nothing like any of the anomalous examples you've seen so far
- Examples of application
	- anomaly detection: fraud detection
	- supervised learning: spam emails