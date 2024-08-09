---
{"topic":"DeepLearning, LargeLanguageModel","dg-publish":true,"permalink":"/Notes/Transformer/","dgPassFrontmatter":true,"noteIcon":""}
---

 
# What is a transformer?

A transformer is a deep learning model architecture. "Transform" means representation is trained and re-used only by changing downstream layers. 
- it is primarily used for natural language processing (NLP) tasks, such as language translation, question-answering, and sentiment analysis. 
- key innovation - "Attention is all you need (2017)": self-attention mechanism
	- it allows the model to focus on different parts of the input sequence at different times during processing. 
	- For example, for NLP, self-attention decides which part of a sentence influences which word, by reweighting the [[Notes/Natural Language Processing#Word embeddings\|Natural Language Processing#Word embeddings]] with interactions between words.

# Types of transformers
## encoder only LLM (autoencoding models)
- pretrained using Masked Language Modeling
- it uses bidirectional context = the model understands the full token
- good for:
	- sentiment analysis
	- names entity recognition
	- word classification
- examples
	- BERT
## decoder only LLM (autoregressive models)
- pretrained using Causal Language Modeling 
- it uses unidirectional context
- good for:
	- text generation
- examples
	- GPT
## encoder decoder LLM (sequence-to-sequence models)
- pretrained using span corruption (e.g. T5)
- good for:
	- translation
	- text summarization 
	- question answering
- examples
	- T5
	- BERT

# Transformer architecture
word embeddings -> positional encoding (multi-head encoding) -> encoder -> decoder

