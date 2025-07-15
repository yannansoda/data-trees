---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Convolutional Neural Networks (CNN)/","dgPassFrontmatter":true,"noteIcon":""}
---


# How it works
![convolutional-nn-1.png|600](/img/user/_assets/images/convolutional-nn-1.png)
### 1. Convolution operation
- convolution operations can make the detector dependent on features and independent of locations -> coarse and invariant detection
- stride ([[Notes/Convolutional Neural Networks (CNN)#Stride\|Convolutional Neural Networks (CNN)#Stride]]) = the moving step size of the feature detector: usually 2
- feature detector = kernel = filter: usually 3x3, but other models such as AlexNet use 7x7
![convolutional-nn-2.png|500](/img/user/_assets/images/convolutional-nn-2.png)

### 2. Pooling
- Pooling = down-sampling = aggregate results over a window of values
- can reduces features and is more robust to overfitting
- types
	- max pooling: represent a subregion by max activation map
		 ![Pasted image 20241001213845.png](/img/user/_assets/images/Pasted%20image%2020241001213845.png)
	- global pooling: reduce spatial dimension to 1
	- aum pooling, Avg Pooling(~subsampling)
- max-pooling is preferable to average pooling, as it confers some degree of invariance to output
- ![convolutional-nn-3.png|500](/img/user/_assets/images/convolutional-nn-3.png)

### 3. Flattening
![convolutional-nn-4.png|500](/img/user/_assets/images/convolutional-nn-4.png)
### 4. Full connection 
The flattened vectors are propagated into an ANN as the input layer
![convolutional-nn-5.png|500](/img/user/_assets/images/convolutional-nn-5.png)


# Size calculation
Assuming that the input shape is $n_h×n_w$ and the convolution kernel shape is $k_h×k_w$, the output shape will be $(n_h−k_h+1)×(n_w−k_w+1)$.
Techniques can also change the output shape:
### Padding
- Padding can increase the height and width of the output 
- padding = add extra pixels of filler around the boundary of our input image, thus increasing the effective size of the image
- ![Pasted image 20241001212305.png](/img/user/_assets/images/Pasted%20image%2020241001212305.png)
- if we add a total of $p_h$ rows of padding (roughly half on top and half on bottom) and a total of $p_w$ columns of padding (roughly half on the left and half on the right), the output shape will be $(n_h−k_h+p_h+1)×(n_w−k_w+p_w+1)$
- In many cases, we will want to set $p_h=k_h-1$ and $p_w=k_w-1$ to give the input and output the same height and width
### Stride
- Stride can reduce the resolution of the output
- stride = the number of rows and columns traversed per slide
- ![Pasted image 20241001212645.png](/img/user/_assets/images/Pasted%20image%2020241001212645.png)
- when the stride for the height is $s_h$ and the stride for the width is $s_w$, the output shape is $[(n_h−k_h+p_h+1)/s_h]×[(n_w−k_w+p_w+1)/s_w]$