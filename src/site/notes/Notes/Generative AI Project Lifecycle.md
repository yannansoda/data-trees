---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/Notes/Generative AI Project Lifecycle/","dgPassFrontmatter":true,"noteIcon":""}
---

## Generative AI project lifecycle
![Pasted image 20240728211236.png|500](/img/user/_assets/images/Pasted%20image%2020240728211236.png)
1. **Define the scope**
2. **Choose an existing model (or pre-train a model)**
	- scaling choices for pre-training
		- goal: maximize model performance
		- constraints: compute budget
		- scaling choice
			- increase dataset size (number of tokens)
			- increase model size (number of parameters)
		- what is found: increasing training dataset size is more important than increasing model size
3. **Prompt engineering: [[Notes/Prompt Engineering\|Prompt Engineering]]**
4. **Fine-tuning (supervised learning/supervised fine-tuning): [[Notes/LLM Finetuning\|LLM Finetuning]]**
5. **Align with human feedback (safety tuning)**
	- goal: HHH = Helpfulness, Honesty, Harmlessness
	- e.g.[[Notes/Reinforcement learning with human feedback (RLHF)\|Reinforcement learning with human feedback (RLHF)]]
6. **Evaluation: [[Notes/Evaluate AI Model & System\|Evaluate AI Model & System]]**
7. **Model optimization and deployment:** 
	- Model-level optimization: [[Notes/LLM Optimization\|LLM Optimization]] (Pre-deployment, optimizing the model itself)
	- Inference-level optimization: [[Notes/AI model Inference Optimization\|AI model Inference Optimization]] (Post-deployment, optimizing model serving and runtime)
8. **Augment model and build LLM-powered applications: [[Notes/LLM-powered Application\|LLM-powered Application]]**












