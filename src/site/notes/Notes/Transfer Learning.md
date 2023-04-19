---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Transfer Learning/","dgPassFrontmatter":true,"noteIcon":""}
---


Transfer learning is the reuse of a pre-trained model on a new problem. 
1. supervised pre-training 
	download neural network with parameters that have been pre-trained on a large dataset with the same input type as your application.
1. fine tuning
	further train the network on your data

> consider somebody else's model trained on a lot more data. They have convolutional layers and they're here intact with features that have already been learned. So you can lock them instead of retraining them on your data, and have those just extract the features from your data using the convolutions that they've already learned. 