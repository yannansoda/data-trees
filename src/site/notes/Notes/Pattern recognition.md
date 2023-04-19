---
{"dg-publish":true,"permalink":"/Notes/Pattern recognition/","noteIcon":""}
---

- to make it more efficient? → convolutional neural networks
- to deal with more complex and real-world images (i.e. megapixel and colored rather than in grayscale) → ImageDataGenerator
- image augmentation introduces a random element to the training images but if the validation set doesn't have the same randomness, then the accuracy fluctuates crazily.

# Avoid overfitting
- image augmentation ([[Notes/Regularization#^933b29\|Regularization#^933b29]])
- dropout ([[Notes/Regularization#^b76d6c\|Regularization#^b76d6c]])
- transfer learning