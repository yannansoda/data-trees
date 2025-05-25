---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Machine Learning All-in-one/","dgPassFrontmatter":true,"noteIcon":""}
---


```toc
```

>[!Quote] What is machine learning?
>- Arthur Samuel 1949 (1901 -1990): Machine Learning is a field of study that gives Computers the ability to learn without being explicitly programmed.
>- Tom Mitchell 1997 (1951 -): Well-posed Learning Problem: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if it is performance on T, as measured by P, improves with experience E.



# Full Cycle of a ML project
1. define project 
2. define and collect data ([[Notes/Data Sampling\|Data Sampling]]) + [[Notes/Data preprocessing\|Data preprocessing]]
3. train model: training, [[Notes/Error analysis\|Error analysis]] & iterative improvement -> loop between 2 and 3 until your model is done
4. deploy in production ([[Notes/Machine Learning Systems Design\|Machine Learning Systems Design]]): deploy, monitor, and maintain system -> back to 3 and/or 2 if needed

# Types of Machine Learning
![Pasted image 20231001114343.png|600](/img/user/_assets/images/Pasted%20image%2020231001114343.png)

# ML Algorithms Cheat Sheet
[[ML+Algorithms+Cheat+Sheet.pdf]]
# Supervised Learning
## Classification
- linear
	- Logistic Regression
	- Support Vector Machine SVM: [[Notes/Support Vector X#Support Vector Machine SVM\|Support Vector X#Support Vector Machine SVM]]
- non-linear
	- Kernel SVM: [[Notes/Support Vector X#Kernels SVM\|Support Vector X#Kernels SVM]]
	- [[Notes/K-Nearest Neighbor\|K-Nearest Neighbor]] (k-NN) 
	- [[Notes/Naive Bayes\|Naive Bayes]]
	- Decision Tree Classification: [[Notes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
	- Random Forest Classification: [[Notes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
- Pros and Cons
![classification-1.png|600](/img/user/_assets/images/classification-1.png)
- Multi-class vs. Multi-label Classification 
## Regression
- Types
	- Linear Regression
	- Polynomial Regression
	-  Regularized regression
		- Lasso regression: [[Notes/Cost Functions#^ed4ab0\|Cost Functions#^ed4ab0]]
		- Ridge regression: [[Notes/Cost Functions#^aef45a\|Cost Functions#^aef45a]]
	- Support Vector Regression (SVR) [[Notes/Support Vector X#^46e7f9\|Support Vector X#^46e7f9]]
	- Decision Tree Regression: [[Notes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
	- Random Forest Regression: [[Notes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
- Pros and Cons
![regression.png|600](/img/user/_assets/images/regression.png)
# Unsupervised Learning
>[!Note]
>The distinction between unsupervised versus self-supervised learning can be blurry sometimes. Roughly:
>- Unsupervised learning attempts to learn representations without labels by not using any targets of any sort during training, e.g. by using correlations in activity between units.
>- Self-supervised learning attempts to learn representations without labels by using the data itself to generate targets, e.g. generating targets using the next word in a sentence
>- Put another way, self-supervised learning looks a lot like supervised learning in code, but there is a big difference related to the following question: do you as a machine learning researcher have to actually ask someone to label the data or not.

## Clustering
- Types
	- [[Notes/Centroid-based Clustering\|Centroid-based Clustering]]: K-Means Clustering
	- [[Notes/Connectivity-based Clustering\|Connectivity-based Clustering]]: Hierarchical Clustering
	- [[Notes/Density-based Clustering\|Density-based Clustering]]: DBSCAN 
	- [[Notes/Graph-based Clustering\|Graph-based Clustering]]: Affinity Propagation
	- [[Notes/Distribution-based Clustering\|Distribution-based Clustering]]: Gaussian Mixture Model
	- [[Notes/Compression-based Clustering\|Compression-based Clustering]]: Spectral Clustering
- Pros and Cons

| Clustering Model | Pros | Cons |
| -- | -- | -- |
| K-Means | interpretability; works well on even-sized and globular-shaped data | need to predefine the number of clusters; not appropriate for outliers; low computation efficiency |
| Hierarchical Clustering | no need to predefine the number of cluster; high computation efficiency; works well on high dimensional data | not appropriate for large data |
| DBSCAN | no need to predefine the number of cluster;  can determine arbitrarily-shaped clusters; can detect outlier | unstable performance (sensitive to density units parameter) |
| Affinity Propagation | no need to predefine the number of cluster | low computation efficiency | low space effciency |
| Gaussian Mixture Model | highest computation efficiency; ensure clusters to follow Gaussian distributions | not appropriate when insufficient data in each cluster |
| Spectral Clustering | high computaion efficiency | need to predefine the number of clusters |
- [[Notes/Clustering Evaluation Metrics\|Clustering Evaluation Metrics]]
## Dimensionality Reduction
- [[Notes/Dimensionality Reduction#Feature Selection\|Dimensionality Reduction#Feature Selection]]
- [[Notes/Dimensionality Reduction#Feature Extraction\|Dimensionality Reduction#Feature Extraction]]
	- Principal Component Analysis (PCA)
	- Linear Discriminant Analysis (LDA)
	- Kernel PCA
	- Quadratic Discriminant Analysis (QDA)
	- T-Distributed Stochastic Neighbor Embedding (t-SNE)
	- Uniform manifold approximation and projection (UMAP)
	- Autoencoders
## Density estimation
## Anomaly detection (see [[Notes/Anomaly detection\|Anomaly detection]])
## Association Rule Learning
- Apriori: [[Notes/Association Rule Learning#Apriori\|Association Rule Learning#Apriori]]
- Eclat: [[Notes/Association Rule Learning#Eclat\|Association Rule Learning#Eclat]]
## Outlier Detection (see [[Notes/Outlier Detection\|Outlier Detection]])

# Ensemble Learning
- Bagging: [[Notes/Ensemble Learning#Bagging (Bootstrap Aggregating)\|Ensemble Learning#Bagging (Bootstrap Aggregating)]]
- Boosting: [[Notes/Ensemble Learning#Boosting\|Ensemble Learning#Boosting]]

# Reinforcement Learning
- Decision making
	- Q-Learning: [[Notes/Reinforcement Learning#Q-Learning\|Reinforcement Learning#Q-Learning]]
	- R Learning
	- TD Learning
- Upper Confidence Bound:  [[Notes/Reinforcement Learning#Upper Confidence Bound\|Reinforcement Learning#Upper Confidence Bound]]
- Thompson Sampling: [[Notes/Reinforcement Learning#Thompson Sampling\|Reinforcement Learning#Thompson Sampling]]

# Deep Learning 
>[!Important]
> - deep learning = training large neural network
> - deep learning is most powerful in supervised learning
> - applications: Advertisement, Images vision, Audio to Text, Machine translation, Autonomous Driving
> - [[Notes/Practical Aspects in Deep Learning\|Practical Aspects in Deep Learning]]

- [[Notes/Artificial Neural Networks\|Artificial Neural Networks]]
- [[Notes/Convolutional Neural Networks\|Convolutional Neural Networks]]
- [[Notes/Recurrent Neural Networks\|Recurrent Neural Networks]]

# Model Selection & Improving
- [[Notes/Cross-Validation\|Cross-Validation]]
- tuning on parameters/[[Notes/Hyperparameter Tuning\|Hyperparameter Tuning]]
	- randomized search
	- grid search
- [[Notes/Ensemble Learning\|Ensemble Learning]]

# ML Model into Production
- [[Notes/Machine Learning Systems Design\|Machine Learning Systems Design]]
- 
# Best Practice for ML

## Be careful about common issues
- **Sample bias**
	- **selection bias**
	- **response bias**
	- real-business scenario: activity bias (social media content), societal bias (human generated content), selection bias (generated by the model itself to form a feedback loop)  
- **Data drift/shift: data distribution shifts**
{ #8a1aad}

	- covariant drift: data distribution of independent variables shifts
	- **label/prior drift**: 
		- data distribution of target variables shifts (the output distribution changes but, for a given output, the input distribution stays the same)
	- **concept/posterior drift**: 
		- the definition of label itself changes based on a particular feature (the input distribution remains the same but the conditional distribution of the output given an input changes)
	- general data distribution shifts
		- feature change
		- label schema change
- **Endogeneity**
	- = a situation where there is a correlation between the predictor variables and the error term in a statistical model.
	- e.g. Rich becomes richer, poor becomes poorer. 
- **Correlation vs. Causation**
- **Multicollinearity**
- **[[Notes/Underfitting vs. Overfitting\|Underfitting vs. Overfitting]]**
## Advanced Practice
- [[Notes/Advanced Practice in ML\|Advanced Practice in ML]]

