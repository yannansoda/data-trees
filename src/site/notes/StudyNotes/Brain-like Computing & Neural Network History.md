---
{"topic":"CompNeuro","dg-publish":true,"permalink":"/StudyNotes/Brain-like Computing & Neural Network History/","dgPassFrontmatter":true,"noteIcon":""}
---

[source](https://zhuanlan.zhihu.com/p/35416350?utm_source=pocket_mylist)
### 第一代神经网络
结合机器学习(SVM, PCA, decision tree..)和神经元模型，最早的神经元网络是由美国计算机科学家罗森布拉特（F.Roseblatt）于1957年提出的感知机（perceptron）。单层感知器是一个具有一层神经元、采用阈值激活函数的前向网络。通过对网络权值的训练，可以使感知器对一组输人矢量的响应达到元素为0或1的目标输出，从而实现对输人矢量分类的目的。感知机具有很强的数学基础，可以理解为多项式回归的变种形式，因为激活函数不可导，所以使用梯度法进行优化，最后得出一组权值参数。
### 第二代神经网络
感知机只能有单层，只能完成线性的分类和回归任务。后来发展出了多层感知机（Multi-layer Perceptron，MLP）并且激活函数使用可微分的sigmod函数代替。但是MLP在提出之初无法训练，因此后来又诞生了著名的反向传播（Back-propergation）算法。MLP可以称为第二代神经网络，也是现在深度学习基础的理论模型。
### 第三代神经网络
类脑计算的研究基础主要是以脉冲神经元模型为基础的神经网络。脉冲神经网络（Spiking Neural Network，SNN）由W.Maass在1997年首次提出，其底层用脉冲函数模仿生物点信号作为神经元之间的信息传递方式，可以算做第三代神经网络。
- SNN的优点是具有更多的生物解释性，一方面可以作为计算神经学对生物脑现象模拟的基础工具；另一方面，由于其信息用脉冲传递的特点，SNN结构更容易在硬件上实现，如FPGA等片上系统（on-chip system）。但是，脉冲函数不可导，因此SNN不能直接应用梯度法进行训练，对SNN的学习算法一直是近年来主要的研究问题。
- SNN主要结构有前馈（Feedforward）和循环链接（Recurrent）两种。
- SNN的神经元模型总体上来说是一类以微分方程构成的模型，带有时间属性。可以理解为传统的神经元只是当前时刻的输入与权重的加权和，SNN的神经元则是在一定宽度的时间窗内的输入与权重的加权和。其中最常见的神经元模型是L&F(Leak and Fire)模型，
