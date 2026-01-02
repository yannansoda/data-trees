---
{"topic":"MachineLearning, DeepLearning, LargeLanguageModel","dg-publish":true,"permalink":"/StudyNotes/Natural Language Processing/","dgPassFrontmatter":true,"noteIcon":""}
---

# Text Preprocessing & Feature Creation
= convert raw text into numeric features suitable for ML models
## Basic Text Preprocessing
- Lowercasing
- Removing punctuation
- Removing stop words (e.g., 'and', 'the', 'is', 'in')
- Stemming/Lemmatization: reduces words to their root form (e.g., 'running' -> 'run', 'studies' -> 'studi')
## Tokenization
= split sequence of characters into “tokens”
- word tokenization
- subword tokenization (BPE, WordPiece): used by modern [[StudyNotes/Transformer\|Transformer]]
- character tokenization
## Creating Features from Text Data
= represent text based on the words it contains
### Bag-of-Words (BoW)
= represents text as a vector of word counts.
- How it works
	1. tokenization
	2. vocabulary building: create a list of all unique tokens
	3. vector creation: create a vector where each element corresponds to the count of a word
### TF–IDF (Term Frequency–Inverse Document Frequency)
= weighted *Bag-of-Words*, which highlights words that are more significant or informative
- How it works
1. **Term Frequency (TF)**: measures the frequency of a term appears in a specific document
2. **Inverse Document Frequency (IDF):** Measures how important a term is across the _entire corpus_.
3. The TF-IDF score is the product of the two.
# Word embeddings
## What are embeddings
- = a type of distributed representation that represent words or text as real-valued vectors in a continuous high-dimensional space
- Words with similar meaning appear close in vector space.
- The simplest word embeddings (word2vec, Glove), map each word to a 300 dimensional vector.
## What to use, and when
- context oblivious: assign one vector per word, regardless of context
	- mostly of historical interest for text
	- examples: Latent Semantic Analysis (LSA), word2vec, fastText
	- Still used for - small datasets, images embeddings
- context sensitive: a word's meaning depends on surrounding context
	- modern NLP
	- examples: BERT and other [[StudyNotes/Transformer\|Transformer]] models
{ #ff7c47}

	- produce embeddings for entire sentences or tokens
# NLP Component Tasks
= core building blocks that many NLP systems rely on
- Part of Speech Tagging (POS tagging)
	- mark the words in the corpus to its corresponding part of a speech tag (noun, verb, adjective, etc), based on its context and definition
- Named Entity Recognition (NER)
	- identify and classify named entities in text into predefined categories such as person names, organization names, locations, dates, etc.
- Co-reference detection
	- identify all the expressions in a text that refer to the same entity
- Parsing
# NLP Problem Types
![natural-language-processing-1.png|600](/img/user/_assets/images/natural-language-processing-1.png)
# Example: Bag-of-Words Workflow

A classical ML approach:
1. Tokenize training text
2. Convert to BoW or TF–IDF vectors
3. Fit a model (e.g., logistic regression)
4. Vectorize test text using the same vocabulary
5. Predict labels (Yes/No, categories, sentiment, etc.)