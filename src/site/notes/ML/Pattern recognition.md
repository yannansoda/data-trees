---
{"dg-publish":true,"permalink":"/ml/pattern-recognition/"}
---

- to make it more efficient? → convolutional neural networks
- to deal with more complex and real-world images (i.e. megapixel and colored rather than in grayscale) → ImageDataGenerator
- image augmentation introduces a random element to the training images but if the validation set doesn't have the same randomness, then the accuracy fluctuates crazily.

# Avoid overfitting
- image augmentation
- dropout
- transfer learning