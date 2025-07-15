---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Pattern Recognition/","dgPassFrontmatter":true,"noteIcon":""}
---

Also called image recognition. Use [[Notes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]].

# Pre-processing techniques
- data normalization:
	- convert numerical representation of pixels to a predefined range, e.g. (0, 1) or (-1, 1)
- image augmentation ([[Notes/Regularization#^933b29\|Regularization#^933b29]])
- image standardization
	- resize to make consistent image sizes 

# Handle imbalance in image data
- merge very similar categories
- resampling ([[Notes/Advanced Practice in ML#^5cfbc3\|Advanced Practice in ML#^5cfbc3]])
- adjust the CNN's loss function to wight mistakes on minority categories more than mistakes on majority categories
# Avoid overfitting
- image augmentation ([[Notes/Regularization#^933b29\|Regularization#^933b29]])
- dropout ([[Notes/Regularization#^b76d6c\|Regularization#^b76d6c]])
- early stopping ([[Notes/Regularization#^9ff80e\|Regularization#^9ff80e]])
- [[Notes/Transfer Learning and Multi-task Learning\|Transfer Learning and Multi-task Learning]]