---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Machine Learning All-in-one/","dgPassFrontmatter":true,"noteIcon":""}
---


```toc
```

>[!Quote] What is machine learning?
>- Arthur Samuel 1949 (1901 -1990): Machine Learning is a field of study that gives Computers the ability to learn without being explicitly programmed.
>- Tom Mitchell 1997 (1951 -): Well-posed Learning Problem: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if it is performance on T, as measured by P, improves with experience E.



# Full Cycle of a ML project
1. define project 
2. define and collect data ([[StudyNotes/Data Sampling\|Data Sampling]]) + [[StudyNotes/Data Preprocessing & Feature Engineering\|Data Preprocessing & Feature Engineering]]
3. train model: training, [[StudyNotes/Error analysis\|Error analysis]] & iterative improvement -> loop between 2 and 3 until your model is done
4. deploy in production ([[StudyNotes/Machine Learning Systems Design\|Machine Learning Systems Design]]): deploy, monitor, and maintain system -> back to 3 and/or 2 if needed

# Types of Machine Learning
![Pasted image 20231001114343.png|600](/img/user/_assets/images/Pasted%20image%2020231001114343.png)

# ML Algorithms Cheat Sheet
[[ML+Algorithms+Cheat+Sheet.pdf]]
# Supervised Learning
## Classification
- linear
	- Logistic Regression
	- Support Vector Machine SVM: [[StudyNotes/Support Vector X#Support Vector Machine SVM\|Support Vector X#Support Vector Machine SVM]]
- non-linear
	- Kernel SVM: [[StudyNotes/Support Vector X#Kernels SVM\|Support Vector X#Kernels SVM]]
	- [[StudyNotes/K-Nearest Neighbor\|K-Nearest Neighbor]] (k-NN) 
	- [[StudyNotes/Naive Bayes\|Naive Bayes]]
	- Decision Tree Classification: [[StudyNotes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
	- Random Forest Classification: [[StudyNotes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
- Pros and Cons
![classification-1.png|600](/img/user/_assets/images/classification-1.png)
- Multi-class vs. Multi-label Classification 
## Regression
- Types
	- Linear Regression
	- Polynomial Regression
	-  Regularized regression
		- Lasso regression: [[StudyNotes/Cost Functions#^ed4ab0\|Cost Functions#^ed4ab0]]
		- Ridge regression: [[StudyNotes/Cost Functions#^aef45a\|Cost Functions#^aef45a]]
	- Support Vector Regression (SVR) [[StudyNotes/Support Vector X#^46e7f9\|Support Vector X#^46e7f9]]
	- Decision Tree Regression: [[StudyNotes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
	- Random Forest Regression: [[StudyNotes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
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
	- [[StudyNotes/Centroid-based Clustering\|Centroid-based Clustering]]: K-Means Clustering
	- [[StudyNotes/Connectivity-based Clustering\|Connectivity-based Clustering]]: Hierarchical Clustering
	- [[StudyNotes/Density-based Clustering\|Density-based Clustering]]: DBSCAN 
	- [[StudyNotes/Graph-based Clustering\|Graph-based Clustering]]: Affinity Propagation
	- [[StudyNotes/Distribution-based Clustering\|Distribution-based Clustering]]: Gaussian Mixture Model
	- [[StudyNotes/Compression-based Clustering\|Compression-based Clustering]]: Spectral Clustering
- Pros and Cons

| Clustering Model        | Pros                                                                                                         | Cons                                                                                               |                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | ------------------- |
| K-Means                 | interpretability; works well on even-sized and globular-shaped data                                          | need to predefine the number of clusters; not appropriate for outliers; low computation efficiency |                     |
| Hierarchical Clustering | no need to predefine the number of cluster; high computation efficiency; works well on high dimensional data | not appropriate for large data                                                                     |                     |
| DBSCAN                  | no need to predefine the number of cluster;  can determine arbitrarily-shaped clusters; can detect outlier   | unstable performance (sensitive to density units parameter)                                        |                     |
| Affinity Propagation    | no need to predefine the number of cluster                                                                   | low computation efficiency                                                                         | low space effciency |
| Gaussian Mixture Model  | highest computation efficiency; ensure clusters to follow Gaussian distributions                             | not appropriate when insufficient data in each cluster                                             |                     |
| Spectral Clustering     | high computaion efficiency                                                                                   | need to predefine the number of clusters                                                           |                     |
- [[StudyNotes/Clustering Evaluation Metrics\|Clustering Evaluation Metrics]]
## Dimensionality Reduction
- [[StudyNotes/Dimensionality Reduction#Feature Selection\|Dimensionality Reduction#Feature Selection]]
- [[StudyNotes/Dimensionality Reduction#Feature Extraction\|Dimensionality Reduction#Feature Extraction]]
	- Principal Component Analysis (PCA)
	- Linear Discriminant Analysis (LDA)
	- Kernel PCA
	- Quadratic Discriminant Analysis (QDA)
	- T-Distributed Stochastic Neighbor Embedding (t-SNE)
	- Uniform manifold approximation and projection (UMAP)
	- Autoencoders
## Density estimation
## [[StudyNotes/Outlier & Anomaly Detection\|Outlier & Anomaly Detection]]

## Association Rule Learning
- Apriori: [[StudyNotes/Association Rule Learning#Apriori\|Association Rule Learning#Apriori]]
- Eclat: [[StudyNotes/Association Rule Learning#Eclat\|Association Rule Learning#Eclat]]
# Ensemble Learning
- Bagging: [[StudyNotes/Ensemble Learning#Bagging (Bootstrap Aggregating)\|Ensemble Learning#Bagging (Bootstrap Aggregating)]]
- Boosting: [[StudyNotes/Ensemble Learning#Boosting\|Ensemble Learning#Boosting]]

# Reinforcement Learning
- Decision making
	- Q-Learning: [[StudyNotes/Reinforcement Learning#Q-Learning\|Reinforcement Learning#Q-Learning]]
	- R Learning
	- TD Learning
- Upper Confidence Bound:  [[StudyNotes/Reinforcement Learning#Upper Confidence Bound\|Reinforcement Learning#Upper Confidence Bound]]
- Thompson Sampling: [[StudyNotes/Reinforcement Learning#Thompson Sampling\|Reinforcement Learning#Thompson Sampling]]

# Deep Learning 
>[!Important]
> - deep learning = training large neural network
> - deep learning is most powerful in supervised learning
> - applications: Advertisement, Images vision, Audio to Text, Machine translation, Autonomous Driving

- Overview: [[StudyNotes/Key Components of Deep Learning\|Key Components of Deep Learning]]
- [[StudyNotes/Artificial Neural Networks\|Artificial Neural Networks]]
- [[StudyNotes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]
- [[StudyNotes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]]

# Model Selection & Improving
- [[StudyNotes/Cross-Validation\|Cross-Validation]]
- tuning on parameters/[[StudyNotes/Hyperparameter Tuning\|Hyperparameter Tuning]]
	- randomized search
	- grid search
- [[StudyNotes/Ensemble Learning\|Ensemble Learning]]

# ML Model into Production
- [[StudyNotes/Machine Learning Systems Design\|Machine Learning Systems Design]]
- 
# Best Practice for ML
- [[StudyNotes/Best Practices & Common Pitfalls in Machine Learning\|Best Practices & Common Pitfalls in Machine Learning]]

