---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Transfer Learning and Multi-task Learning/","dgPassFrontmatter":true,"noteIcon":""}
---

# Transfer Learning
Transfer learning is the reuse of a pre-trained model on a new problem. 
1. supervised pre-training 
	download neural network with parameters that have been pre-trained on a large dataset with the same input type as your application.
2. finetuning ([[StudyNotes/LLM Finetuning\|LLM Finetuning]])
	further train the network on your data

> consider somebody else's model trained on a lot more data. They have convolutional layers and they're here intact with features that have already been learned. So you can lock them instead of retraining them on your data, and have those just extract the features from your data using the convolutions that they've already learned. 

# Multi-task Learning
Different from transfer learning, multi-task learning uses one neural network for several things at the same time. 

It helps when
- training on a set of tasks that could benefit from having shared lower-level features
- the amount of data for each task is quite similar
- train a big enough neural network to do well on all the tasks

example: in computer vision, detect lots of different objects using one neural network, instead of several networks that only detect one object each.
