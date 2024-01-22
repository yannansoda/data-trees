---
{"topic":"DataScience","dg-publish":true,"permalink":"/Notes/Data Sampling/","dgPassFrontmatter":true,"noteIcon":""}
---

- Non-probabilistic sampling
- Simple random sampling
- Stratified sampling
- Weighted sampling
- Importance sampling
- Reservoir sampling
	- especially useful for streaming data
	- The algorithm involves a reservoir, which can be an array, and consists of three steps:
		- Put the first k elements into the reservoir.
		- For each incoming nth element, generate a random number i such that 1 ≤ i ≤ n.
		- If 1 ≤ i ≤ k: replace the ith element in the reservoir with the nth element. Else, do nothing.![Pasted image 20230626150930.png|500](/img/user/assets/images/Pasted%20image%2020230626150930.png)