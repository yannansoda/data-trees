---
{"topic":"Math, MachineLearning","dg-publish":true,"permalink":"/LearningNotes/Dimensionality Reduction/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"Math, MachineLearning"}}
---


# What is Dimensionality Reduction
Dimensionality reduction reduces the number of input features while preserving as much meaningful information as possible. 

There are two main approaches:
- [[LearningNotes/Dimensionality Reduction#Feature Selection\|Feature Selection]]: keep some original features
- [[LearningNotes/Dimensionality Reduction#Feature Extraction\|Feature Extraction]]: create new lower-dimensional features

# Feature Selection
= selects a subset of the original features based on their importance, relevance, or redundancy

See [[LearningNotes/Feature selection\|Feature selection]] for detailed methods.

Main types:
- **Filter methods**: use statistical scores before modeling
- **Wrapper methods**: search feature subsets using model performance
- **Embedded / Intrinsic methods**: feature selection happens during model training

# Feature Extraction
= transforms original features into a lower-dimensional space using mathematical techniques
## Linear / Matrix-based Methods
### Principal Component Analysis (PCA)
linear technique that finds orthogonal components maximizing variance in the data
#### Component Selection Criteria
= decides how many principal components to keep
- **Scree plot**: plot eigenvalues / explained variance and keep components before the curve becomes flat (the "elbow")
- **Kaiser rule**: keep any component with eigenvalue above 1, usually when features are standardized
- **Cumulative variance threshold**: keep the smallest number of components that explain enough total variance, e.g. 80-95%
### Singular Value Decomposition (SVD) / Truncated SVD
matrix factorization method that finds lower-rank structure in data
- often used for sparse data, text data, and recommender systems
- similar goal to PCA, but Truncated SVD can work without centering sparse matrices
### Independent Component Analysis (ICA)
finds components that are statistically independent, not just uncorrelated
- useful when signals are mixed together, e.g. separating audio / brain signals
### Non-negative Matrix Factorization (NMF)
factorizes data into non-negative parts-based components
- useful for topic modeling, images, and count-like data
### Random Projection
projects data into a lower-dimensional space using a random matrix
- fast approximation, useful when the original data is very high-dimensional

## Supervised Projection
### Linear Discriminant Analysis (LDA)
supervised method that projects data to maximize class separability
- max number of components = number of classes - 1
- it creates new axes to maximize the class-separation, step by step (2-class example):
	1. maximize the distance between class means $\mu_1$ and $\mu_2$
	2. minimize the variation (which LDA calls "scatter") within each class $s_1$ and $s_2$
	3. compute $\frac{(\mu_1 - \mu_2)^2}{s_1^2 + s_2^2 }$ (=$\frac{d_{1,2}^2}{s_1^2 + s_2^2 }$) and LDA should maximize it 
	4. if more than 2 classes, e.g. there are 3 classes, the value to be maximized will be $\frac{d_{1,2}^2 + d_{1,3}^2 + d_{2,3}^2}{s_1^2 + s_2^2 + s_3^2}$

> [!Tip] PCA vs. LDA
>
{ #dbef75}

> - PCA captures the variability; LDA class separation
> - PCA is unsupervised; LDA is supervised (because of the relation to the dependent variable)
>  
![dimensionality-reduction-1.png\|400](/img/user/_assets/images/dimensionality-reduction-1.png)
![dimensionality-reduction-2.png\|400](/img/user/_assets/images/dimensionality-reduction-2.png) 

## Non-linear / Manifold Learning
### Kernel PCA
extends PCA using kernel methods to capture non-linear patterns
### t-Distributed Stochastic Neighbor Embedding (t-SNE)
non-linear dimensionality reduction method mainly used for visualization in 2D/3D, optimized for preserving local structure
- t-SNE takes high-dimensional data and reduces it to low-dimensional coordinates (2-D typically)
- it calculates a similarity measure based on the distance between points instead of trying to maximize variance.
- Unlike PCA (which is linear), t-SNE can reduce dimensions with non-linear relationships (such as “Swiss Roll” non-linear distribution)
- mainly for visualization, not usually for creating features for a predictive model
![Pasted image 20230609142126.png\|200](/img/user/_assets/images/Pasted%20image%2020230609142126.png)
### Uniform Manifold Approximation and Projection (UMAP)
- fast and scalable non-linear dimensionality reduction method, preserves both global and local structure
- similar to t-SNE but faster and often better at retaining overall shape
### Isomap
non-linear manifold learning method that preserves geodesic distances on a manifold
### Locally Linear Embedding (LLE)
non-linear manifold learning method that preserves local neighborhood relationships
### Multidimensional Scaling (MDS)
places points in lower dimensions while preserving pairwise distances as much as possible

## Neural Network-based
### Autoencoders: see [[LearningNotes/Autoencoders\|Autoencoders]]
neural network-based models that learn a compressed latent representation through reconstruction

## Related but not really dimensionality reduction
### Quadratic Discriminant Analysis (QDA)
similar to LDA but assumes each class has its own covariance matrix, allowing quadratic decision boundaries
- not really a dimensionality reduction method; more commonly used as a classifier
