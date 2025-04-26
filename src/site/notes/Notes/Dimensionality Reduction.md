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

## **PCA** vs. **LDA**
{ #dbef75}


- PCA capture the variability; LDA class separation
	![dimensionality-reduction-1.png|400](/img/user/_assets/images/dimensionality-reduction-1.png)
	![dimensionality-reduction-2.png|400](/img/user/_assets/images/dimensionality-reduction-2.png)
{ #9ffa4d}

- PCA is unsupervised; LDA is supervised (because of the relation to the dependent variable)
- How LDA works exactly
	- it creates new axes to maximize the class-separation, step by step (2-class example):
		1. maximize the distance between class means $\mu_1$ and $\mu_2$
		2. minimize the variation (which LDA calls "scatter") within each class $s_1$ and $s_2$
		3. compute $\frac{(\mu_1 - \mu_2)^2}{s_1^2 + s_2^2 }$ (=$\frac{d_{1,2}^2}{s_1^2 + s_2^2 }$) and LDA should maximize it 
		4. if more than 2 classes, e.g. there are 3 classes, the value to be maximized will be $\frac{d_{1,2}^2 + d_{1,3}^2 + d_{2,3}^2}{s_1^2 + s_2^2 + s_3^2}$
## t-SNE 
{ #53a070}

- = T-Distributed Stochastic Neighbor Embedding
- t-SNE takes high-dimensional data and reduces it to a low-dimensional graph (2-D typically)
- Unlike PCA (which is linear), t-SNE can reduce dimensions with non-linear relationships (such as “Swiss Roll” non-linear distribution)
	- ![Pasted image 20230609142126.png|200](/img/user/_assets/images/Pasted%20image%2020230609142126.png)
- it calculates a similarity measure based on the distance between points instead of trying to maximize variance.
