---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Transforming Algorithms/","dgPassFrontmatter":true,"noteIcon":""}
---


There are generally two groups of transforming algorithms: 
- Feature-transforming algorithms
	- learn some mathematical function that takes features as an input and then combines and transforms them to produce an output that matches the target values in the training set.
	- e.g. Linear regression and neural nets, PCA (Principal Component Analysis), LDA (Linear Discriminant Analysis)
	- feature transformers generally can extrapolate target values beyond the training set given appropriate features as inputs
- Target-transforming algorithms
	- use the features to group the target values in the training set and make predictions by averaging values in a group; a set of feature just indicates which group to average. 
	- e.g. Decision trees and nearest neighbors 
	- target transformers will always be bound within the range of the training set and cannot extrapolate 