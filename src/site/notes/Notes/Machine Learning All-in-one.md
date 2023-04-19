---
{"dg-publish":true,"permalink":"/Notes/Machine Learning All-in-one/","noteIcon":""}
---


# Full Cycle of a ML project
1. define project 
2. define and collect data
3. train model: training, error analysis & iterative improvement -> loop between 2 and 3 until your model is done
4. deploy in production: deploy, monitor, and maintain system -> back to 3 and/or 2 if needed



# Supervised Learning
## Classification
### linear
- Logistic Regression
- Support Vector Machine SVM: [[Notes/Support Vector X#Support Vector Machine SVM\|Support Vector X#Support Vector Machine SVM]]
### non-linear
- Kernel SVM: [[Notes/Support Vector X#Kernels SVM\|Support Vector X#Kernels SVM]]
-  [[Notes/K-Nearest Neighbor\|K-Nearest Neighbor]] (k-NN) 
- [[Notes/Naive Bayes\|Naive Bayes]]
- Decision Tree Classification: [[Notes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
- Random Forest Classification: [[Notes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]

### Pros and Cons
![assets/images/classification-1.png|600](/img/user/assets/images/classification-1.png)

## Regression
- Linear Regression
- Polynomial Regression
- Support Vector Regression (SVR) [[Notes/Support Vector X#^46e7f9\|Support Vector X#^46e7f9]]
- Decision Tree Regression: [[Notes/Decision Tree & Random Forest#Decision Tree\|Decision Tree & Random Forest#Decision Tree]]
- Random Forest Regression: [[Notes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]]
- Regularized regression
	- Lasso regression
	- Ridge regression

### Pros and Cons
![regression.png|600](/img/user/assets/images/regression.png)

# Unsupervised Learning
## Clustering
- [[Notes/K-Means Clustering\|K-Means Clustering]] (an example of Partitional Clustering)
- [[Notes/Hierarchical Clustering\|Hierarchical Clustering]]

### Pros and Cons
![clustering.png|600](/img/user/assets/images/clustering.png)

# Association Rule Learning
- Apriori: [[Notes/Association Rule Learning#Apriori\|Association Rule Learning#Apriori]]
- Eclat: [[Notes/Association Rule Learning#Eclat\|Association Rule Learning#Eclat]]

# Reinforcement learning
- Upper Confidence Bound:  [[Notes/Reinforcement learning#Upper Confidence Bound\|Reinforcement learning#Upper Confidence Bound]]
- Thompson Sampling: [[Notes/Reinforcement learning#Thompson Sampling\|Reinforcement learning#Thompson Sampling]]
- Decision making
	- Q-Learning
	- R Learning
	- TD Learning

# Natural Language Processing

# Deep Learning 
>[!Important]
> - deep learning = training large neural network
> - deep learning is most powerful in supervised learning
> - applications: Advertisement, Images vision, Audio to Text, Machine translation, Autonomous Driving
> - [[Practical Aspects in Deep Learning\|Practical Aspects in Deep Learning]]

- [[Notes/Artificial Neural Networks\|Artificial Neural Networks]]
- [[Notes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]
- [[Notes/Dimensionality Reduction\|Dimensionality Reduction]]:
	- Feature Selection
	- Feature Extraction
		- Principal Component Analysis (PCA)
		- Linear Discriminant Analysis (LDA)
		- Kernel PCA
		- Quadratic Discriminant Analysis (QDA)
- Linear Discriminant Analysis


# Model Selection & Boosting
- k-fold cross validation
	- accuracy [[Notes/Confusion Matrix#Accuracy\|Confusion Matrix#Accuracy]] is used as a standard 
- tuning on parameters/[[Notes/Hyperparameter Tuning\|Hyperparameter Tuning]]
	- randomized search
	- grid search
- Boosting 
	- an ensemble method for improving the weak model predictions of any given learning algorithm.
	- XGBoost ([[Notes/Gradient boosting algorithm#XGBoost vs Gradient Boosting\|Gradient boosting algorithm#XGBoost vs Gradient Boosting]]) 

# Applications
- [[Notes/ML in Bioinformatics\|ML in Bioinformatics]]