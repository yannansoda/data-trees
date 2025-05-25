---
{"topic":"Math, MachineLearning","dg-publish":true,"permalink":"/Notes/Dimensionality Reduction/","dgPassFrontmatter":true,"noteIcon":""}
---


# What is Dimensionality Reduction
Dimensionality reduction reduces the number of input features while preserving as much meaningful information as possible. 

There are two main approaches:
- [[Notes/Dimensionality Reduction#Feature Selection\|Feature Selection]]
- [[Notes/Dimensionality Reduction#Feature Extraction\|Feature Extraction]]
# Feature Selection
= selects a subset of the original features based on their importance, relevance, or redundancy
## Methods
- **Forward Selection**: Add features one by one based on performance improvement
- **Backward Elimination**: Start with all features and remove the least useful
- **Bidirectional Elimination**: Combines forward selection and backward elimination.
- **Score Comparison**: Use statistical or model-based scores (e.g., ANOVA F-test, mutual information).

# Feature Extraction
=  transforms original features into a lower-dimensional space using mathematical techniques
## Methods
- **Principal Component Analysis (PCA)**
	- linear technique that finds orthogonal components maximizing variance in the data
- **Linear Discriminant Analysis (LDA)**
	- supervised method that projects data to maximize class separability
- **Quadratic Discriminant Analysis (QDA)**
	- similar to LDA but assumes each class has its own covariance matrix, allowing quadratic decision boundaries
- **Kernel PCA**
	- extends PCA using kernel methods to capture non-linear patterns
- **t-Distributed Stochastic Neighbor Embedding (t-SNE)**
	- non-linear technique for visualizing high-dimensional data in 2D/3D, optimized for preserving local structure
- **Uniform Manifold Approximation and Projection (UMAP)**
	- fast and scalable non-linear dimensionality reduction method, preserves both global and local structure
	- similar to t-SNE but faster and often better at retaining overall shape
- **Autoencoders**
	- neural network-based models that learn a compressed latent representation through reconstruction

## PCA vs. LDA
{ #dbef75}

### Comparison
- PCA capture the variability; LDA class separation
	![dimensionality-reduction-1.png|400](/img/user/_assets/images/dimensionality-reduction-1.png)
	![dimensionality-reduction-2.png|400](/img/user/_assets/images/dimensionality-reduction-2.png) 
- PCA is unsupervised; LDA is supervised (because of the relation to the dependent variable)
### How LDA works exactly
- it creates new axes to maximize the class-separation, step by step (2-class example):
	1. maximize the distance between class means $\mu_1$ and $\mu_2$
	2. minimize the variation (which LDA calls "scatter") within each class $s_1$ and $s_2$
	3. compute $\frac{(\mu_1 - \mu_2)^2}{s_1^2 + s_2^2 }$ (=$\frac{d_{1,2}^2}{s_1^2 + s_2^2 }$) and LDA should maximize it 
	4. if more than 2 classes, e.g. there are 3 classes, the value to be maximized will be $\frac{d_{1,2}^2 + d_{1,3}^2 + d_{2,3}^2}{s_1^2 + s_2^2 + s_3^2}$

## t-Distributed Stochastic Neighbor Embedding (t-SNE)
- t-SNE takes high-dimensional data and reduces it to a low-dimensional graph (2-D typically)
- - it calculates a similarity measure based on the distance between points instead of trying to maximize variance.

- Unlike PCA (which is linear), t-SNE can reduce dimensions with non-linear relationships (such as “Swiss Roll” non-linear distribution)
![Pasted image 20230609142126.png|200](/img/user/_assets/images/Pasted%20image%2020230609142126.png)
