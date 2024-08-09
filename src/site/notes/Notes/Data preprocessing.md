---
{"topic":"Data Science, MachineLearning","dg-publish":true,"permalink":"/Notes/Data preprocessing/","dgPassFrontmatter":true,"noteIcon":""}
---


# Data labelling
- correctly labeled datasets are often called "ground truth"
- efficient data labelling
	- access to additional human workforces: [[Notes/Machine Learning Systems Design#Human-in-the-Loop Pipelines\|Machine Learning Systems Design#Human-in-the-Loop Pipelines]]
	- automated data labelling capabilities
	- assistive labelling features
# Data preprocessing techniques for ML

### 1. taking care of **missing data**
There are several ways to handle missing data:
- delete missing rows/columns 
	- when the size of the data set will not decrease substantially unless filter them out would bias the sample
- data imputation
{ #594d05}

	- use mean/median for continuous value
	- use mode for discrete value
	- use specific values within/out of the range
	- regression imputation: predict the value by building an interpolator or predicting them based on other features
- use missing value as a separate feature

### 2. handle outliers 
- removal: outlier-containing entries are deleted from the distribution
- replacing  handle as missing values and replac with suitable imputation
- capping: use an arbitrary value or a value from a variable distribution to replace the maximum and minimum values
- discretization:  convert continuous variables, models, and functions into discrete one, by constructing a series of continuous intervals (or bins) that span the range of our desired variable/model/function

### 3. log transform
- turn a skewed distribution into a normal or less-skewed distribution

### 4. **categorical encoding** = converting categorical columns to numerical columns 

- two approaches
	- Label encoding
	- One-hot encoding
- choices of approaches
	- Label encoding is suitable when:
		- the categorical feature is ordinal
		- the number of categories is quite large (high cardinality)
	- One-hot encoding is suitable when:
		- the categorical feature is not ordinal 
		- the number of categories is quite small (low cardinality)
 	
> [!Challenges of One-Hot Encoding]
> - **Dummy Variable Trap**: a scenario in which the independent variables are multicollinear:  -> so, always omit one dummy variable!
> - **Cannot Capture Interaction Effects**: fix this by creating composite feature and computing explicit feature crosses

> [!In Python practice, use categorical data type] 
> It saves a ton of memory space by using category data type instead of object.
### 5. splitting datasets into the training and test sets

### 6. **feature scaling**
= a method used to normalize the range of independent variables or features of data
#### two options
- standardization 
	- = z-score normalization (universal) = subtract mean and divide by standard deviation => afterwards the data follow Normal(0, 1)
	- easy to choose sensible priors (then you can detect small slope values like 0.5)
	- computation works better
	- only apply to normal distribution

$$
x' = \frac{x - \bar x}{ \sigma}
$$
- normalization 
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


# What is Feature Engineering then?
Feature engineering = selecting, extracting, and transforming the most relevant features from the available data to build 
Thus, the techniques above can belong to feature engineering. Besides, there are feature creation and feature extraction/selection:
- Feature creation
	- feature Interaction: create new features by combining already existing features
	- feature aggregation: create summarized features, such as the mean of standard deviation
- [[Notes/Feature selection\|Feature selection]]

>[!Careful] Best practice for feature engineering
> - avoid [[Notes/Data Leakage\|Data Leakage]]
> - use statistics from only the train split, instead of the entire data, to scale your features and handle missing values
> - handle imbalanced data: [[Notes/Advanced Practice in ML#Handling imbalanced dataset\|Advanced Practice in ML#Handling imbalanced dataset]]
> - handle Difference in Proportions of Labels (DPL)
> - keep track of data lineage: [[Notes/Advanced Practice in ML#Data lineage\|Advanced Practice in ML#Data lineage]]
> - use features that generalize well: [[Notes/Advanced Practice in ML#Important for feature engineering Making Feature Generalization\|Advanced Practice in ML#Important for feature engineering Making Feature Generalization]]


