---
{"topic":"MachineLearning, DeepLearning","dg-publish":true,"permalink":"/Notes/Transformer/","dgPassFrontmatter":true,"noteIcon":""}
---

 
# What is a transformer?

A transformer is a deep learning model architecture. "Transform" means representation is trained and re-used only by changing downstream layers. 
- it is primarily used for natural language processing (NLP) tasks, such as language translation, question-answering, and sentiment analysis. 
- key innovation - "Attention is all you need (2017)": self-attention mechanism
	- it allows the model to focus on different parts of the input sequence at different times during processing. 
	- For example, for NLP, self-attention decides which part of a sentence influences which word, by reweighting the [[Notes/Natural Language Processing#Word embeddings\|Natural Language Processing#Word embeddings]] with interactions between words.
# Transformer architecture
word embeddings -> positional encoding (multi-head encoding) -> encoder -> decoder