---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Natural Language Processing/","dgPassFrontmatter":true,"noteIcon":""}
---


# NLP component tasks
- Tokenization
	- split sequence of characters into “tokens”
- Part of Speech Tagging (POS tagging)
	- mark the words in the corpus to its corresponding part of a speech tag (noun, verb, adjective, etc), based on its context and definition
- Named Entity Recognition (NER)
	- identify and classify named entities in text into predefined categories such as person names, organization names, locations, dates, etc.
- Co-reference detection
	- identify all the expressions in a text that refer to the same entity
- Parsing

# Word embeddings
## what are embeddings
- Word embeddings are a type of distributed representation that represents words or phrases as real-valued vectors in a high-dimensional space. 
- The simplest word embeddings (word2vec, Glove), map each word to a 300 dimensional vector such that words that are tend to show up in the same contexts have embeddings that are close to each other.
## what to use, when
- context oblivious: mostly of historical interest for text
	- Latent Semantic Analysis (LSA), word2vec, fastText
	- Still used for images
- context sensitive: pick a popular embedding from Hugging Face
	- BERT and other transformer models
	- These use a context oblivious Byte Pair or Word Part Encoding as input


# NLP Types
![](/img/user/assets/images/natural-language-processing-1.png)
# Example: Bag-of-Words Model
To answer Yes/No, transform test words into a count array, then use training data arrays to model a logistic regression and then predict Yes/No responses.
