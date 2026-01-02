---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Model Offline Evaluation/","dgPassFrontmatter":true,"noteIcon":""}
---

# Evaluation methods
- Perturbation tests
	- make small changes to your test splits to see how these changes affect your model’s performance
- In-variance tests
	- certain changes to the inputs shouldn’t lead to changes in the output.
- Directional expectation tests
	- e.g.if x increases, y is expected to decrease; if not, you should check before deploying it
- Model calibration
	- a common method is Platt scaling
- Confidence measurement
	- think about the usefulness threshold for each individual prediction
- Slice-based evaluation
	- consider Simpson’s paradox
	- issues
		- model performs differently on different slices of data when the model should perform the same
		- model performs the same on different slices of data when the model should perform differently
	- thus, you should discover critical slices in your data using
		- heuristics-based approach: slice the data using domain knowledge
		- [[StudyNotes/Error analysis\|Error analysis]]: manually go through misclassified examples and find patterns among them
		- slice finder