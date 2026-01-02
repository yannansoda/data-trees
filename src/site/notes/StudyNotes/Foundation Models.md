---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/StudyNotes/Foundation Models/","dgPassFrontmatter":true,"noteIcon":""}
---


## Basics & Terms
### Model architecture: [[StudyNotes/Transformer\|Transformer]] 
### Model scale
The scale of a model can be measured by three key numbers:
- model size
	- the number of parameters
	- usually billions of parameters
- token size
	- the number of training tokens
	- usually trillions of tokens
- the number of Floating point operation (FLOP) needed for training
	- **What is FLOP**
		- the number of floating point operations performed for a certain task
		- as a standard unit for a model's compute requirement
		- note that FLOP/s is a different thing: it means floating point operations per second, which measures a machine's peak performance
- given a compute budget, the optimal number of parameters and number of tokens can be determined with [[StudyNotes/Scaling Law\|Scaling Law]] 

## Pre-training & Post-training
### Pre-training
- = train a model from scratch, where the model weights are randomly initialized
### Post-training
- = train a previously trained model, where the model weights are obtained from the previous training process
- Two steps
	1. **Supervised finetuning (SFT)**: finetune the pre-trained model on high-quality instruction data
	2. **Preference finetuning**: further finetune the model to output responses that align with human preference, e.g. by [[StudyNotes/Reinforcement learning with human feedback (RLHF)\|Reinforcement learning with human feedback (RLHF)]]

## Sampling
- = the process that a model constructs its outputs
- sampling makes AI models probabilistic -> the probabilistic nature of AI -> inconsistency & *hallucinations*
- greedy vs. random sampling
	- **greedy sampling** = always picking the most likely outcome
		- the same input will always produce the same output
		- not ideal for LLM
	- **random sampling** = sample the outcome with probability
### Random sampling strategies
- **temperature scaling**
{ #27bdb5}

	- affect the randomness of the output of the softmax layer in [[StudyNotes/Transformer\|Transformer]]
	- typically between 0 and 2
		- temperature =0 -> reliability
		- temperature >0 -> variety
		- 0.7 is often recommended
- **top-k sampling**
	- pick the top-k probability and perform softmax over these top-k probability only
- **top-p sampling**
	- pick the top values that sum to probability $p$ and perform softmax over these top-p probability only
	- $p$ typically range from 0.9 to 0.95
