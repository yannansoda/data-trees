---
{"topic":"MachineLearning, DeepLearning","dg-publish":true,"permalink":"/StudyNotes/Long Short Term Memory/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Resources]
>[Video: Long Short-Term Memory (LSTM), Clearly Explained](https://youtu.be/YCzL96nL7j0?feature=shared)

### What is LSTM
- It is a type of [[StudyNotes/Recurrent Neural Networks (RNN)\|Recurrent Neural Networks (RNN)]] architecture
- It is designed to address the vanishing/exploding gradient problem (see [[StudyNotes/Optimization Algorithms#^4a1546\|Optimization Algorithms#^4a1546]]) in traditional RNNs, allowing it to effectively capture long-term dependencies in sequential data.


### Long vs Short
- why "long": It is a unique structure with memory cells that can store and access information over long periods
- long-term memories = cell states: no weights, thus to avoid vanishing/exploding gradients
- short-term memories = hidden states: with weights, just as vanilla RNNs

### LSTM units
[illustration figure 1](https://medium.com/analytics-vidhya/lstms-explained-a-complete-technically-accurate-conceptual-guide-with-keras-2a650327e8f2)
![Pasted image 20240827222030.png](/img/user/_assets/images/Pasted%20image%2020240827222030.png)
[illustration figure 2](https://youtu.be/YCzL96nL7j0?feature=shared)
![Pasted image 20240827221918.png](/img/user/_assets/images/Pasted%20image%2020240827221918.png)
#### three key components
- input gates
	- activation function is tanh (-1 to 1)
	- even though this part determines how we should update the long-term memory....
- forget gates 
	 - activation function is sigmoid (0 to 1)
	 - decides what percentage of the long-term memory is remembered
- output gates