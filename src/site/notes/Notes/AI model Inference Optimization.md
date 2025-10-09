---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/Notes/AI model Inference Optimization/","dgPassFrontmatter":true,"noteIcon":""}
---

## Inference performance metrics
### Latency metrics
= measure the time from when users send a query until they receive the complete response
- The overall latency can be broken into several metrics:
	- **Time to first token (TTFT)** = how quickly the first token is generated after users send a query
	- **Time per output token** = how quickly each output token is generated after the first token
	- **Time between tokens** and **inter-token latency** = the time between output tokens
### Utilization metrics
= measure how efficiently a resource is being used
- **MFU (Model FLOP/s Utilization)** = the ratio of the observed throughput (tokens/s) relative to the theoretical maximum throughput of a system operating at peak FLOP/s
- **MBU (Model Bandwidth Utilization)** = the percentage of achievable memory bandwidth used
## Inference Optimization
Inference optimization can be done at different levels:
- model level
- hardware level
- service level
### Inference model optimization
- optimize model size
	- model compression
- optimize autoregressive decoding
	- speculative decoding
	- inference with reference
	- parallel decoding
- optimize attention mechanism
	- attention mechanism optimization
	- redesigning the attention mechanism
	- writing kernels for attention computation
### Inference service optimization
- batching
- decoupling prefill and decode
- prompt caching
- parallelism