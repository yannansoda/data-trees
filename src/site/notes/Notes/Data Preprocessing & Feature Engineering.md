---
{"topic":"Data Science, MachineLearning","dg-publish":true,"permalink":"/Notes/Data Preprocessing & Feature Engineering/","dgPassFrontmatter":true,"noteIcon":""}
---


# Data preprocessing techniques & pipeline for ML

### 1. Data Quality & Data Leakage Checks

- Identify and remove columns that cause [[Notes/Data Leakage\|Data Leakage]] (post-event data, target-derived features).
- *Data lineage* = a technique that helps keep track of the origin of each of data samples as well as its labels
- Perform early sanity checks:
    - impossible values
    - duplicate rows / duplicate entities
    - violations of constraints
### 2. Handling missing data
#### Understanding why data is missing
- **Missing Completely At Random (MCAR)**: probability being missing depends on both the observed values of other features and the unobserved missing value itself
- **Missing At Random (MAR)**: probability being missing depends on _only_ on the observed values of _other_ features, not on the missing value itself
- **Missing Not At Random (MNAR):** probability being missing depends on the missing value itself or on other unobserved factors
#### Ways of handling missing data
- **delete missing rows/columns** 
	- when the size of the data set will not decrease substantially unless filter them out would bias the sample
- **data imputation**
{ #594d05}

	- Mean / Median / Mode Imputation
		- use mean/median for continuous value
		- use mode for discrete value
	- use specific values within/out of the range
	- regression imputation: predict the value by building an interpolator or predicting them based on other features
		- stochastic regression imputation: enhanced regression imputation, where *Imputed Value=Regression Prediction + Random Error*
	- advanced imputation techniques
		- [[Notes/K-Nearest Neighbor\|K-Nearest Neighbor]] imputation
		- Multiple Imputation by Chained Equations (MICE) / Iterative Imputation
- **create missing value (binary) indicators**
>[!tip]
> To prevent data leakage, always perform imputation after splitting your data into training and test sets. 
### 3. Handling Outliers 
- **removal**: outlier-containing entries are deleted from the distribution
- **replacing**: handle as missing values and replace with suitable imputation
- **capping**: use an arbitrary value or a value from a variable distribution to replace the maximum and minimum values
- **discretization**: convert continuous variables, models, and functions into discrete one, by constructing a series of continuous intervals (or bins) that span the range of our desired variable/model/function
- also see [[Notes/Outlier Detection\|Outlier Detection]]
### 4. Splitting datasets into the training and test sets
### 5. Categorical Encoding
= converting categorical columns to numerical columns 
> [!In Python practice, use categorical data type] 
> It saves a ton of memory space by using category data type instead of object.

#### Common approaches
- Label encoding
- One-hot encoding
- choices of approaches
	- Label encoding is suitable when:
		- the categorical feature is ordinal
		- the number of categories is quite large (high cardinality)
	- One-hot encoding 
		- suitable when:
			- the categorical feature is not ordinal 
			- the number of categories is quite small (low cardinality)
		- challenges of One-Hot Encoding
			- **Dummy Variable Trap**: a scenario in which the independent variables are multicollinear:  -> so, always omit one dummy variable! 
			- **Cannot Capture Interaction Effects**: fix this by creating composite feature and computing explicit feature crosses
#### Other techniques
- target encoding (mean encoding)
	- group data by the categorical feature -> calculate the mean of the target variable for each group -> replace the category label with this calculated mean
- binary encoding
- hashing encoder
### 6. Feature Scaling
= a method used to normalize the range of independent variables or features of data
#### standardization 
- = z-score normalization (universal) = subtract mean and divide by standard deviation => afterwards the data follow Normal(0, 1)
- easy to choose sensible priors (then you can detect small slope values like 0.5)
- computation works better
- only apply to normal distribution

$$
x' = \frac{x - \bar x}{ \sigma}
$$
#### normalization
- = min-max scaling / min-max normalization
- preserve the shape of the dataset
$$
x' = \frac{x - min(x)}{max(x) - min(x)}
$$
>[!Quote] Which to choose, from *The Hundred-Page Machine Learning Book*
>- unsupervised learning algorithms, in practice, more often benefit from standardization than from normalization
>- standardization is also preferred for a feature if the values this feature takes are distributed close to a normal distribution (so-called bell curve)
>- again, standardization is preferred for a feature if it can sometimes have extremely high or low values (outliers); this is because normalization will “squeeze” the normal values into a very small range
>- In all other cases, normalization is preferable.”

#### Why use feature scaling
It is optional, but beneficial to gradient descent and calculation speed; useful in at least three circumstances:
- for algorithms that use Euclidian distance: Kmeans, KNN: different scales distort the calculation of distance.
- for algorithms that optimize with gradient descent: features in different scales make gradient descent harder to converge.
- for dimensionality reduction (PCA): finds combinations of features that have the most variance
>[!Important]
>- don’t apply feature scaling on dummy variables!
>- better apply feature scaling on train and test dataset separately, in case of [[Notes/Data Leakage\|Data Leakage]].

### 7. Transforming Skewed Feature Distributions
- **Log Transformation**: turn a skewed distribution into a normal or less-skewed distribution
- **Box–Cox Transformation**; positive values only
- **Yeo–Johnson Transformation**: similar to Box-Cox but works with negative values
### 8. Feature Engineering

= selecting, extracting, and transforming the most relevant features from the available data to build, *after raw data is clean and normalized*
- **Feature creation**
	- feature Interaction: create new features by combining already existing features
	- feature aggregation: create summarized features, such as the mean of standard deviation
- **[[Notes/Feature selection\|Feature selection]]**
#### Best practice for feature engineering
- avoid [[Notes/Data Leakage\|Data Leakage]]
- use statistics from only the train split, instead of the entire data, to scale your features and handle missing values
- handle imbalanced data: [[Notes/Best Practices & Common Pitfalls in Machine Learning#Imbalanced Datasets\|Best Practices & Common Pitfalls in Machine Learning#Imbalanced Datasets]]
- Data-level: undersampling, oversampling, SMOTE, ADASYN
- Algorithm-level: cost-sensitive learning, focal loss
- Feature generalization:  [[Notes/Best Practices & Common Pitfalls in Machine Learning#Feature Generalization\|Best Practices & Common Pitfalls in Machine Learning#Feature Generalization]]
	- Feature coverage: how often the feature is present
	- Distribution generalization: feature works across many population slices
- handle Difference in Proportions of Labels (DPL)
- keep track of data lineage
