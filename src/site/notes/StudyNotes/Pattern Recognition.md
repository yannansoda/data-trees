---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Pattern Recognition/","dgPassFrontmatter":true,"noteIcon":""}
---

Also called image recognition. Use [[StudyNotes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]].

# Pre-processing techniques
- data normalization:
	- convert numerical representation of pixels to a predefined range, e.g. (0, 1) or (-1, 1)
- image augmentation ([[StudyNotes/Regularization#^933b29\|Regularization#^933b29]])
- image standardization
	- resize to make consistent image sizes 

# Handle imbalance in image data
- merge very similar categories
- resampling ([[StudyNotes/Best Practices & Common Pitfalls in Machine Learning#^5cfbc3\|Best Practices & Common Pitfalls in Machine Learning#^5cfbc3]])
- adjust the CNN's loss function to wight mistakes on minority categories more than mistakes on majority categories
# Avoid overfitting
- image augmentation ([[StudyNotes/Regularization#^933b29\|Regularization#^933b29]])
- dropout ([[StudyNotes/Regularization#^b76d6c\|Regularization#^b76d6c]])
- early stopping ([[StudyNotes/Regularization#^9ff80e\|Regularization#^9ff80e]])
- [[StudyNotes/Transfer Learning and Multi-task Learning\|Transfer Learning and Multi-task Learning]]