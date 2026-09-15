---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/LearningNotes/Machine Learning All-in-one/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"MachineLearning"}}
---



>[!Quote] What is machine learning?
>- Arthur Samuel 1949 (1901 -1990): Machine Learning is a field of study that gives Computers the ability to learn without being explicitly programmed.
>- Tom Mitchell 1997 (1951 -): Well-posed Learning Problem: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if it is performance on T, as measured by P, improves with experience E.

# Full Cycle of a ML project
1. define project 
2. define and collect data ([[LearningNotes/Data Sampling\|Data Sampling]]) + [[LearningNotes/Data Preprocessing & Feature Engineering\|Data Preprocessing & Feature Engineering]]
3. train model: training, [[LearningNotes/Error analysis\|Error analysis]] & iterative improvement -> loop between 2 and 3 until your model is done
4. deploy in production ([[LearningNotes/Machine Learning Systems Design\|Machine Learning Systems Design]]): deploy, monitor, and maintain system -> back to 3 and/or 2 if needed


# ML Algorithms Cheat Sheet
[ML+Algorithms+Cheat+Sheet.pdf](/img/user/_assets/images/ML+Algorithms+Cheat+Sheet.pdf)
# Learning Paradigms
> *Where does feedback come from?*
## Supervised Learning
### Classification
- linear
	- Logistic Regression
	- Support Vector Machine SVM: [[LearningNotes/Support Vector X#Support Vector Machine SVM\|Support Vector X#Support Vector Machine SVM]]
- non-linear
	- Kernel SVM: [[LearningNotes/Support Vector X#Kernels SVM\|Support Vector X#Kernels SVM]]
	- [[LearningNotes/K-Nearest Neighbor\|K-Nearest Neighbor]] (k-NN) 
	- [[LearningNotes/Naive Bayes\|Naive Bayes]]
	- Decision Tree Classification: [[LearningNotes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
	- Random Forest Classification: [[LearningNotes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
- Pros and Cons
![classification-1.png\|600](/img/user/_assets/images/classification-1.png)
- Multi-class vs. Multi-label Classification 
### [[LearningNotes/Regression\|Regression]]
- Types
	- Linear Regression
	- Polynomial Regression
	-  Regularized regression
		- Lasso regression: [[LearningNotes/Regression#Lasso Regression\|Regression#Lasso Regression]]
		- Ridge regression: [[LearningNotes/Regression#Ridge Regression\|Regression#Ridge Regression]]
	- Support Vector Regression (SVR) [[LearningNotes/Support Vector X#^46e7f9\|Support Vector X#^46e7f9]]
	- Decision Tree Regression: [[LearningNotes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
	- Random Forest Regression: [[LearningNotes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
- Pros and Cons
![regression.png\|600](/img/user/_assets/images/regression.png)
## Unsupervised Learning

### Clustering
- Types
	- [[LearningNotes/Centroid-based Clustering\|Centroid-based Clustering]]: K-Means Clustering
	- [[LearningNotes/Connectivity-based Clustering\|Connectivity-based Clustering]]: Hierarchical Clustering
	- [[LearningNotes/Density-based Clustering\|Density-based Clustering]]: DBSCAN 
	- [[LearningNotes/Graph-based Clustering\|Graph-based Clustering]]: Affinity Propagation
	- [[LearningNotes/Distribution-based Clustering\|Distribution-based Clustering]]: Gaussian Mixture Model
	- [[LearningNotes/Compression-based Clustering\|Compression-based Clustering]]: Spectral Clustering
- Pros and Cons

| Clustering Model        | Pros                                                                                                         | Cons                                                                                               |                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | ------------------- |
| K-Means                 | interpretability; works well on even-sized and globular-shaped data                                          | need to predefine the number of clusters; not appropriate for outliers; low computation efficiency |                     |
| Hierarchical Clustering | no need to predefine the number of cluster; high computation efficiency; works well on high dimensional data | not appropriate for large data                                                                     |                     |
| DBSCAN                  | no need to predefine the number of cluster;  can determine arbitrarily-shaped clusters; can detect outlier   | unstable performance (sensitive to density units parameter)                                        |                     |
| Affinity Propagation    | no need to predefine the number of cluster                                                                   | low computation efficiency                                                                         | low space effciency |
| Gaussian Mixture Model  | highest computation efficiency; ensure clusters to follow Gaussian distributions                             | not appropriate when insufficient data in each cluster                                             |                     |
| Spectral Clustering     | high computaion efficiency                                                                                   | need to predefine the number of clusters                                                           |                     |
- [[LearningNotes/Clustering Evaluation Metrics\|Clustering Evaluation Metrics]]
### Dimensionality Reduction
- [[LearningNotes/Dimensionality Reduction#Feature Selection\|Dimensionality Reduction#Feature Selection]]
- [[LearningNotes/Dimensionality Reduction#Feature Extraction\|Dimensionality Reduction#Feature Extraction]]
	- Principal Component Analysis (PCA)
	- Linear Discriminant Analysis (LDA)
	- Kernel PCA
	- Quadratic Discriminant Analysis (QDA)
	- T-Distributed Stochastic Neighbor Embedding (t-SNE)
	- Uniform manifold approximation and projection (UMAP)
	- Autoencoders
### Density Estimation
see [[LearningNotes/Density Estimation\|Density Estimation]]
### Anomaly Detection
see [[LearningNotes/Outlier & Anomaly Detection\|Outlier & Anomaly Detection]]
### Association Rule Learning
- Apriori: [[LearningNotes/Association Rule Learning#Apriori\|Association Rule Learning#Apriori]]
- Eclat: [[LearningNotes/Association Rule Learning#Eclat\|Association Rule Learning#Eclat]]

## Semi-Supervised Learning
- **dataset**: partially labeled, with some data points having labels and others being unlabeled
- **how it works**
	- use the labeled data to learn patterns and then generalize those patterns to the unlabeled data
	- minimizes the difference in predictions between similar training examples
- **approaches**
	- self-training
	- co-training
	- multi-view learning
## Self-Supervised Learning
- algorithm learns from the data without explicit human annotations
>[!Note]
>The distinction between unsupervised versus self-supervised learning can be blurry sometimes. Roughly:
>- Unsupervised learning attempts to learn representations without labels by not using any targets of any sort during training, e.g. by using correlations in activity between units.
>- Self-supervised learning attempts to learn representations without labels by using the data itself to generate targets, e.g. generating targets using the next word in a sentence
>- Put another way, self-supervised learning looks a lot like supervised learning in code, but there is a big difference related to the following question: do you as a machine learning researcher have to actually ask someone to label the data or not.
- **approaches**
	- Contrastive Learning
	- Pretext-task Learning
## Reinforcement Learning
### Decision making
- Q-Learning: [[LearningNotes/Reinforcement Learning#Q-Learning\|Reinforcement Learning#Q-Learning]]
- R Learning
- TD Learning
### Upper Confidence Bound
see [[LearningNotes/Reinforcement Learning#Upper Confidence Bound\|Reinforcement Learning#Upper Confidence Bound]]
### Thompson Sampling
[[LearningNotes/Reinforcement Learning#Thompson Sampling\|Reinforcement Learning#Thompson Sampling]]
# Learning Settings
> *How is data received or labeled?*

- Batch Learning
- Online Learning
- Active Learning
- [[LearningNotes/ML System Monitoring and Continual learning\|Continual Learning]]

# Generalization Strategies
> *How does knowledge move across tasks?*
- Inductive Learning
- Transductive Learning
- Deductive Inference
- [[LearningNotes/Transfer Learning and Multi-task Learning\|Transfer Learning]]
- [[LearningNotes/Transfer Learning and Multi-task Learning\|Multi-Task Learning]]
- Few-Shot Learning
- Zero-Shot Learning
- Multi-Instance Learning
# Modeling Frameworks
- Discriminative Learning
- Generative Learning
- Representation Learning
- Bayesian Learning
- Hebbian Learning
# Model Families
## Classical ML Models
- Linear models
- Trees
- SVM
- Naive Bayes
- k-NN
## Ensemble Methods
- Bagging: [[LearningNotes/Ensemble Learning#Bagging (Bootstrap Aggregating)\|Ensemble Learning#Bagging (Bootstrap Aggregating)]]
- Boosting: [[LearningNotes/Ensemble Learning#Boosting\|Ensemble Learning#Boosting]]
- Random Forest: [[LearningNotes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
- [[LearningNotes/Gradient Boosting\|Gradient Boosting]]
## Deep Learning 
>[!Important]
> - deep learning = training large neural network
> - deep learning is most powerful in supervised learning
> - applications: Advertisement, Images vision, Audio to Text, Machine translation, Autonomous Driving

- Overview: [[LearningNotes/Key Components of Deep Learning\|Key Components of Deep Learning]]
- [[LearningNotes/Artificial Neural Networks\|Artificial Neural Networks]]
- [[LearningNotes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]
- [[LearningNotes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]]
- [[LearningNotes/Transformer\|Transformer]]
- [[LearningNotes/Autoencoders\|Autoencoders]]
- [[LearningNotes/Generative Adversarial Networks (GANs)\|Generative Adversarial Networks (GANs)]]
- [[LearningNotes/Variational Autoencoders (VAE)\|Variational Autoencoders (VAE)]]

# Model Selection & Improving
- [[LearningNotes/Cross-Validation\|Cross-Validation]]
- [[LearningNotes/Hyperparameter Tuning\|Hyperparameter Tuning]]
	- randomized search
	- grid search
- [[LearningNotes/Error analysis\|Error analysis]]
- [[LearningNotes/Error Metrics\|Error Metrics]]
- [[LearningNotes/Bias-Variance Tradeoff\|Bias-Variance Tradeoff]]
- [[LearningNotes/Underfitting vs. Overfitting\|Underfitting vs. Overfitting]]
- [[LearningNotes/Data Leakage\|Data Leakage]]

# ML Model into Production
see  [[LearningNotes/Machine Learning Systems Design\|Machine Learning Systems Design]]
- [[LearningNotes/ML Model Deployment\|ML Model Deployment]]
- [[LearningNotes/ML System Monitoring and Continual learning\|ML System Monitoring and Continual learning]]
# Best Practice for ML
- [[LearningNotes/Best Practices & Common Pitfalls in Machine Learning\|Best Practices & Common Pitfalls in Machine Learning]]

