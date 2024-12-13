---
{"topic":"LargeLanguageModel","dg-publish":true,"permalink":"/Notes/Retrieval Augmented Generation (RAG)/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is RAG
RAG is a technique in natural language processing (NLP) that combines retrieval-based and generation-based methods.
- "reterival-based" means that, unlike purely generative models that create responses from scratch, retrieval-based systems rely on accessing existing data or knowledge to formulate their outputs 
![Pasted image 20240614172114.png](/img/user/assets/images/Pasted%20image%2020240614172114.png) (image [source](https://towardsdatascience.com/rag-vs-finetuning-which-is-the-best-tool-to-boost-your-llm-application-94654b1eaba7))

### Why RAG is needed
- LLM faces challenges
	- domain knowledge
	- hallucinations
	- training date cut off (outdated training set)
- These challenges maybe can be tackled by [[Notes/LLM Fine-tuning\|LLM Fine-tuning]], but it's expensive to train the LLM
> [! llm Fine-tuning]
![Pasted image 20240614172423.png](/img/user/assets/images/Pasted%20image%2020240614172423.png)  (image [source](https://towardsdatascience.com/rag-vs-finetuning-which-is-the-best-tool-to-boost-your-llm-application-94654b1eaba7))

### Data for RAG 
#### RAG integrates with many types of data sources
- documents
- wikis
- expert systems
- web pages
- databases
- vector store (vector representation of text)
#### Data preparation for RAG
- data must fit inside context window
- data must be in format that allows its relevance to be assessed at inference time 