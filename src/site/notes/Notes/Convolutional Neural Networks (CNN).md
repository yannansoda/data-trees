---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Convolutional Neural Networks (CNN)/","dgPassFrontmatter":true,"noteIcon":""}
---


# How it works
![](/img/user/assets/images/convolutional-nn-1.png)
1. Convolution operation
![](/img/user/assets/images/convolutional-nn-2.png)
>- stride = the moving step size of the feature detector: usually 2
>- feature detector = kernel = filter :usually 3x3, but other models such as AlexNet use 7x7
2. Pooling
Pooling(=down-sampling) can reduces features and is more robust to overfitting.
![](/img/user/assets/images/convolutional-nn-3.png)

types: max pooling, aum Pooling, Avg Pooling(~subsampling)
3. Flattening
![](/img/user/assets/images/convolutional-nn-4.png)
4. Full connection 
The flattened vectors are propagated into an ANN as the input layer
![](/img/user/assets/images/convolutional-nn-5.png)