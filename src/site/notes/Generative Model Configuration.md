---
{"topic":"LargeLanguageModel","dg-publish":true,"permalink":"/Generative Model Configuration/","dgPassFrontmatter":true,"noteIcon":""}
---

In LLM, we can experiment with generative configuration parameters to influence the way that the model makes the final decision about next-word generation

generative configuration parameters for inference 
- max new tokens
- greedy vs. random sampling
- top-k sampling vs. top-p samplingfin
- temperature
{ #1ce105}

	- affect the randomness of the output of the softmax layer in [[Notes/Transformer\|Transformer]]
	- temperature =0 -> reliability
	- temperature >0 -> variety