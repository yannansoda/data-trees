---
{"topic":"DataScience","dg-publish":true,"permalink":"/StudyNotes/Outlier & Anomaly Detection/","dgPassFrontmatter":true,"noteIcon":""}
---

# Outlier vs. Anomaly
- Outlier detection focuses on identifying **statistically extreme points**.  
- Anomaly detection focuses on identifying **contextually unusual behavior or events**.
- All anomalies may be outliers, but not all outliers are anomalies.
# Outlier Detection
## Univariate outlier detection
### Z-score / Standard Score
- commonly, values with Z-scores beyond a threshold (e.g., ±3) are considered outliers
### Interquartile Range (IQR) Method
- Values below $Q1− 1.5 \times \text{IQR}$ or above $Q3+1.5 \times \text{IQR}$ are considered outliers.
## Multivariate outlier detection
### Mahalanobis Distance
- Measures the distance of a point from the mean of a multivariate distribution, considering correlations among variables 
- Higher values of the Mahalanobis distance indicate potential outliers
### PCA
- see [[StudyNotes/Dimensionality Reduction#**PCA** vs. **LDA**\|Dimensionality Reduction#**PCA** vs. **LDA**]]
- identify data points that deviate from the pattern of the majority after transformation
### Elliptic Envelope (Robust Covariance)
- fits an elliptical envelope to the data and classifies points outside it as outliers, assuming a Gaussian distribution
### FPOF (Fixed-Point Outlier Factor)
- a density-based outlier detection method: detect outliers by comparing the density of each point with those around it
- outlier = a point has a significantly lower count within a fixed radius 
### Counts Outlier Detector
- tracks how frequently each data point or observation appears in the dataset
- outlier = points with unusually low or high counts (depending on the context) 
- suitable for categorical data or discrete datasets
### Distance Metric Learning
- supervised or semi-supervised learning to label outliers
- aims to learn an optimal distance metric (often a Mahalanobis distance or similar) that maximizes the separation of normal and anomalous points based on certain criteria or labeled examples of outliers
- perform well on complex or high-dimensional data
### Shared Nearest Neighbors (SNN)
- a graph-based approach that calculates the similarity between each pair of data points by examining how many neighbors they share
- outlier = points with few or no shared neighbors in common with other points
- perform well on complex or high-dimensional data

# Anomaly Detection (Contextual / Model-Based)
## Types of Anomalies
- Point Anomalies
- Contextual Anomalies (Conditional Anomalies): considered anomalous only within a specific context
- Collective Anomalies: a set of related data being anomalous as a group
## Detection Methods
### Probabilistic Modeling
Fit density model $p(x)$ on training set and predict
- anomaly: $y = 1$ if $p(x) < \epsilon$
- normal: $y = 0$ if $p(x) >= \epsilon$
- density models
	- Gaussian models
	- Gaussian Mixture Models
	- KDE (Kernel Density Estimation)
### Machine Learning-Based Methods
- One-Class SVM (Support Vector Machine)
- Isolation Forest
- [[StudyNotes/Autoencoders\|Autoencoders]] (reconstruction error)
### Doping (Synthetic Anomalies)
- a strategy that introduces synthetic samples ("doped points" or "artificial outliers") into the dataset to help train a model to better distinguish between normal data points and anomalies
## Evaluating Anomaly Detection
Use standard metrics from classification:
- True Positive (TP)
- False Positive (FP)
- Precision, Recall
- F1-score (see [[StudyNotes/Confusion Matrix#F1-score\|Confusion Matrix#F1-score]])
## Anomaly detection vs. supervised learning
Why bother using anomaly detection rather than supervised learning if your examples already have labels?
- Anomaly detection is more proper than supervised learning, when:
	- very small number of anomalous examples
	- future anomalies may look nothing like any of the anomalous examples you've seen so far
- Examples of application
	- anomaly detection: fraud detection
	- supervised learning: spam emails