---
{"topic":"DeepLearning","dg-publish":true,"permalink":"/Notes/Key Components of Deep Learning/","dgPassFrontmatter":true,"noteIcon":""}
---

## Overview of key components
- Objective function
- Learning rule
- Architecture
- Initialisation
- Environment 

## Objective Function (Loss/Cost Function)
= quantifies how well the neural network's predictions match the expected outputs.
- Common examples (see [[Notes/Cost Functions\|Cost Functions]])
    - **Cross-entropy loss**: for classification problems
    - **Mean squared error (MSE)**: for regression tasks
    - **Contrastive or triplet loss**: for representation learning or similarity-based tasks
- Often augmented with **regularization terms** to prevent overfitting ([[Notes/Cost Functions#Cost function with regularization\|Cost Functions#Cost function with regularization]])
## Learning Rule (Optimization Algorithm)
 = dictates how the model updates its parameters (weights and biases) to minimize the objective function.
 - The optimizer plays a critical role in the **convergence speed** and **stability** of training.
- It typically involves:
    - **Gradient computation**: via [[Notes/Artificial Neural Networks#How it works\|Artificial Neural Networks#How it works]]
    - **Parameter updates**: using optimizers such as Adam ([[Notes/Gradient Descent#Variants of Gradient Descent\|Gradient Descent#Variants of Gradient Descent]])
- The learning rule is sensitive to:
    - **Learning rate** (step size)
    - **Momentum** ([[Notes/Gradient Descent#Momentum\|Gradient Descent#Momentum]])
    - **Batch size**
## Architecture (Model Structure)
= **layout and connectivity** of the network — how many layers, how many neurons per layer, and how the layers are connected.
- Common architectural types

| Architecture                                                            | Input Type                     | Handles Sequence?    | Task Type                                              | Supervised?               | Typical Use Cases                                            |
| ----------------------------------------------------------------------- | ------------------------------ | -------------------- | ------------------------------------------------------ | ------------------------- | ------------------------------------------------------------ |
| **Feedforward Neural Networks (FNNs)** (simple multi-layer perceptrons) | Tabular / vector data          | No                   | Discriminative (classification, regression)            | Yes                       | Credit scoring, house price prediction                       |
| [[Notes/Convolutional Neural Networks (CNN)\|Convolutional Neural Networks (CNN)]]                                 | Spatial (images, videos)       | No                   | Discriminative / Generative                            | Yes / (some unsupervised) | Image classification, segmentation, image generation         |
| [[Notes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]]                                     | Sequential (text, time series) | Yes                  | Discriminative                                         | Yes                       | Sentiment analysis, language modeling, stock prediction      |
| [[Notes/Transformer\|Transformer]]                                                         | Sequential (text, audio)       | Yes (via attention)  | Discriminative & Generative                            | Yes / No                  | Translation, summarization, protein folding, chatbots        |
| [[Notes/Autoencoders\|Autoencoders]]                                                        | Any (images, text, signals)    | No / Yes (with RNNs) | Generative / Feature Learning                          | No                        | Denoising, anomaly detection, dimensionality reduction       |
| [[Notes/Variational Autoencoders (VAE)\|Variational Autoencoders (VAE)]]                                      | Any (images, text, signals)    | No / Yes (with RNNs) | Generative / Feature Learning / Probabilistic Modeling | No                        | Generative modeling, smooth latent space, data generation    |
| [[Generative Adversarial Networks (GANs)\|Generative Adversarial Networks (GANs)]]                              | Any (often images)             | No / Yes             | Generative                                             | No                        | Image generation, data augmentation, synthetic data creation |


- Design choices include:
    - **Activation functions** (ReLU, Sigmoid, Tanh, see [[Notes/Artificial Neural Networks#Activation functions\|Artificial Neural Networks#Activation functions]])
    - **Depth and width**
    - **Skip connections** (e.g., in ResNets)
    - **Normalization layers** (BatchNorm, LayerNorm)

## Initialization (Starting Point for Learning)
= refers to how the network’s weights are set before training begins.
- Good initialization helps avoid issues like:
    - **Vanishing/exploding gradients** ([[Notes/Optimization Algorithms#^4a1546\|Optimization Algorithms#^4a1546]])
    - **Slow convergence**
- Common initialization strategies:
    - **Xavier/Glorot Initialization**: for balanced signal flow.
    - **He Initialization**: tailored for ReLU activations.
    - **Pretrained weights**: from transfer learning or self-supervised learning.
- Bias terms are often initialized to zero or small constants.
## Environment (Training Data and Learning Context)
= defines the **input data**, **labels**, and **context** the model is exposed to during learning.
- Key aspects:
    - **Type and quality of data** (structured, unstructured, labeled, noisy).
    - **Supervised, unsupervised, or reinforcement learning setup**.
    - **Batching and shuffling** of data.
    - **Data augmentation** to increase diversity and prevent overfitting.
    - **Train/validation/test splits** to assess generalization.
- In [[Notes/Reinforcement Learning\|Reinforcement Learning]], the "environment" refers to the interactive system where the agent takes actions and receives feedback (rewards).