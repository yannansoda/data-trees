---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/Notes/LLM Optimization/","dgPassFrontmatter":true,"noteIcon":""}
---

### LLM optimization techniques
#### distillation
- = a larger teacher model train a smaller student model.
- the student model learns to statistically mimic the behavior of the teacher model
	- either just in the final prediction layer 
	- or in the model's hidden layers as well
- typically effective for encoder-only models
- ![Pasted image 20240811215348.png|400](/img/user/_assets/images/Pasted%20image%2020240811215348.png)
#### quantization
- = reduce weight's precision
- example: Post-Traning Quantization (PTQ)
- ![Pasted image 20240811215701.png|400](/img/user/_assets/images/Pasted%20image%2020240811215701.png)
#### pruning 
- = remove model weights with values close or equal to 0
- pruning methods
	- full model re-training
	- PEFT/LoRA ([[Notes/LLM Finetuning#PEFT techniques\|LLM Finetuning#PEFT techniques]])
	- Post-training ([[Notes/Foundation Models#Post-training\|Foundation Models#Post-training]])
- in theory vs. in practice
	- in theory, it can reduce model size and improve performance
	- in practice, only small % in LLMs are 0-weights