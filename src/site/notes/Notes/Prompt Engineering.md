---
{"topic":"LargeLanguageModel","dg-publish":true,"permalink":"/Notes/Prompt Engineering/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Source]
> [ChatGPT Prompt Engineering for Developers](https://learn.deeplearning.ai/courses/chatgpt-prompt-eng)
## Two types of LLMs
- Base LLM
	- predicts next word based on text training data
- Instruction tuned LLM
	- fine-tune on instructions and good attempts at following instructions 
	- e.g.[[Notes/Reinforcement learning with human feedback (RLHF)\|Reinforcement learning with human feedback (RLHF)]] 

## Prompting Principles
### Principle 1: Write clear and specific instructions
- Tactic 1: Use delimiters to clearly indicate distinct parts of the input
	- Delimiters can be anything like: ```, """, < >, <tag> </tag>, :
- Tactic 2: Ask for a structured output (JSON, HTML, etc)
- Tactic 3: Ask the model to check whether conditions are satisfied
- Tactic 4: "Few-shot" prompting
	- provide desired output before giving the prompt
### Principle 2: Give the model time to “think”
- Tactic 1: Specify the steps required to complete a task
	- step 1: ...
	- step 2: ...
- Tactic 2: Instruct the model to work out its own solution before rushing to a conclusion

## In-context learning/prompting methods
 - **zero-shot prompting**: creating an initial prompt that states the task to be completed but not includes examples
 - **one/few shot prompting**: creating an initial prompt that states the task to be completed and includes a single/few of example question with answer
 - **chain-of-thought prompting**: creating a prompt that demonstrates how to solve similar problems using step-by-step reasoning

## Iterative Prompt Development
![Pasted image 20240718150823.png|400](/img/user/assets/images/Pasted%20image%2020240718150823.png)

## Capabilities of LLM
### Summarizing
- Summarizing
- Extracting
### Inferring
examples: 
- “What is the sentiment of the following …”
- “Determine five topics that are being discussed in the following test…”
### Transforming
- Translation
- Tone Transformation
- File Format Conversion
- Spellcheck/Grammar Check
### Expanding
= generate long piece of text from short piece of text
### Temperature
= degree of randomness of the model (see [[Generative Model Configuration#^1ce105\|Generative Model Configuration#^1ce105]])
- use temperature 0 for tasks that require reliability, predictability
- use temperature >0 for tasks that require variety



