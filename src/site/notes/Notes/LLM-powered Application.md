---
{"topic":"LargeLanguageModel","dg-publish":true,"permalink":"/Notes/LLM-powered Application/","dgPassFrontmatter":true,"noteIcon":""}
---

### Using LLM in applications
![Pasted image 20240812093815.png|500](/img/user/assets/images/Pasted%20image%2020240812093815.png)
- LLM can interact with external datasets: 
	- e.g. [[Notes/Retrieval Augmented Generation (RAG)\|Retrieval Augmented Generation (RAG)]]
- LLM can interact with external applications
	- examples
		- trigger API call
		- perform calculations
	- requirements for using LLMs to power applications
		- plan actions
		- format outputs
		- validate actions: collect required information and make sure it is in the completion


### LLM application architectures
![Pasted image 20240812220730.png|500](/img/user/assets/images/Pasted%20image%2020240812220730.png)

### Use LLMs to power an application through reasoning and action planning
- use chain of thought prompting to help LLMs improve their reasoning
- program-aided language models (PAL)
	- = an LLM with an external code interpreter to carry out calculation
	- the LLM generate completions where reasoning steps are accompanied by computer code
	- as an example of LLM interacting with external applications
- ReAct
	- a prompting strategy that combines chain of thought reasoning with action planning
	- the number of actions is limited: defined by a set of instructions that is pre-pended to the example prompt text
