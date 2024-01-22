---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Convolutional Neural Networks (CNN)/","dgPassFrontmatter":true,"noteIcon":""}
---


# How it works
![](/img/user/assets/images/convolutional-nn-1.png)
### 1. Convolution operation
- convolution operations can make the detector dependent on features and independent of locations -> coarse and invariant detection
- stride = the moving step size of the feature detector: usually 2
- feature detector = kernel = filter :usually 3x3, but other models such as AlexNet use 7x7
![/assets/images/convolutional-nn-2.png|500](/img/user/assets/images/convolutional-nn-2.png)

### 2. Pooling
- Pooling(=down-sampling) can reduces features and is more robust to overfitting.
- types
	- max pooling: represent a subregion by max activation map
	- global pooling: reduce spatial dimension to 1
	- aum pooling, Avg Pooling(~subsampling)
![/assets/images/convolutional-nn-3.png|500](/img/user/assets/images/convolutional-nn-3.png)

### 3. Flattening
![/assets/images/convolutional-nn-4.png|500](/img/user/assets/images/convolutional-nn-4.png)
### 4. Full connection 
The flattened vectors are propagated into an ANN as the input layer
![/assets/images/convolutional-nn-5.png|500](/img/user/assets/images/convolutional-nn-5.png)