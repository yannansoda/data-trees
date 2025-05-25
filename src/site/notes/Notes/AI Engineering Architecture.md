---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/Notes/AI Engineering Architecture/","dgPassFrontmatter":true,"noteIcon":""}
---

## The simplest architecture 
In its simplest form:
1. an application receives a query
2. sends it to the model API
3. model generates a response 
4. response is returned to the user

## More components can be added
### 1. Enhance context
_Placed between query and model API_: Enhance context input into a model by giving the model access to external data sources and tools
- via [[Notes/Retrieval Augmented Generation (RAG)\|Retrieval Augmented Generation (RAG)]]
- via tools that allow the model to automatically gather information through APIs such as web search
>[!Quote]
>Context construction is like feature engineering for foundation models.
### 2. Put in guardrails
_Placed at inputs and outputs_: Guardrails help protect you and your users
- input guardrails
	- protect against two types of risks 
		- leaking private information to external APIs
		- executing bad prompts that compromise your system
	- how it works
		- e.g. sensitive data is detected by AI tools -> the entire query is blocked or the sensitive information is removed 
- output guardrails
	- catch output failures: quality failure / security failure
	- specify the policy to handle different failure modes
### 3. Add model router and gateway
_Placed inside the model_: they support complex pipelines and add more security
### 4. Reduce latency and cost with caches
_Placed inside the model_: typically implemented by model API providers
- major system caching mechanisms: 
	- exact caching
	- semantic caching
### 5. Add agent patterns
_Placed in a loop_: the system's output may not be enough to accomplish the task so it starts another cycle (similar to [[Notes/Intelligent Agent\|Intelligent Agent]])