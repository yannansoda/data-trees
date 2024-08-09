---
{"topic":"Math, MachineLearning","dg-publish":true,"permalink":"/Notes/Dimensionality Reduction/","dgPassFrontmatter":true,"noteIcon":""}
---


There are two types of Dimensionality Reduction techniques:  
- Feature selection
- Feature extraction
# Feature Selection
- Backward Elimination, Forward Selection, Bidirectional
- Elimination, Score Comparison

# Feature Extraction
- PCA vs. LDA
	- PCA capture the variability; LDA class separation
		![/assets/images/dimensionality-reduction-1.png|400](/img/user/assets/images/dimensionality-reduction-1.png)
		![/assets/images/dimensionality-reduction-2.png|400](/img/user/assets/images/dimensionality-reduction-2.png)
{ #9ffa4d}

	- PCA is unsupervised; LDA is supervised (because of the relation to the dependent variable)
- t-SNE 
{ #53a070}

	- = T-Distributed Stochastic Neighbor Embedding
	- t-SNE takes high-dimensional data and reduces it to a low-dimensional graph (2-D typically)
	- Unlike PCA (which is linear), t-SNE can reduce dimensions with non-linear relationships (such as “Swiss Roll” non-linear distribution)
		- ![Pasted image 20230609142126.png|200](/img/user/assets/images/Pasted%20image%2020230609142126.png)
	- it calculates a similarity measure based on the distance between points instead of trying to maximize variance.
