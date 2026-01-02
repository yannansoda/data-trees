---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/StudyNotes/Evaluate AI Model & System/","dgPassFrontmatter":true,"noteIcon":""}
---

## Language modelling metrics
### [[StudyNotes/Entropy\|Entropy]]
### Cross-entropy ([[StudyNotes/Entropy#^c91fe9\|Entropy#^c91fe9]])
- in language model, cross entropy (with unit in bits) represents how many bits this language model needs to represent each token
### Bits-per-Character & Bits-per-Byte
- Bits-per-Character = the number of bits per token / the number of characters per token
- Bits-per-Byte = the number of bits per token / the number of bits per token
### Perplexity
- = the exponential of entropy (and cross entropy) 
- given a distribution $P$ $$PPL(P) = 2^{H(P)}$$
- in language model, it measures the amount of uncertainty it has when predicting the next token
- Interpretations
	- more structured data gives lower expected perplexity
	- the bigger the vocabulary, the higher the perplexity
	- the longer the context length, the lower the perplexity
## Task-specific evaluation metrics
### Metrics
- ROUGE
	- used for text summarization
	- compares a summary to one or more reference summaries
- BLEU SCORE
	- used for text translation
	- compares to human-generated translations
	- =avg(across range of n-gram sizes)
### Evaluation benchmarks
- GLUE, SuperGLUE
- massive multitask language understanding
- BIG-bench
- holistic evaluation of language models (HELM)
## Evaluating open-ended responses
### Exact evaluation: produces judgment without ambiguity
- functional correctness
- similarity measurements against reference data
	- reference data: generated typically by humans but also from human-reviewed AI
### Subjective evaluation
- **AI as a judge** = using AI to evaluate AI
- ranking models with comparative evaluation

## Evaluating AI systems
### Evaluation criteria
- domain-specific capability
- generation capability
- instruction-following capability
- cost and latency
### Model selection
Evaluation workflow at a high level:
1. filter out models with hard attributes
2. use publicly available information, e.g., public benchmark performance
3. run experiments with task-specific evaluation
4. continually monitor the model in production

