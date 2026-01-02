---
{"topic":"LargeLanguageModel, AIEngineering","dg-publish":true,"permalink":"/StudyNotes/Intelligent Agent/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is Agent
- An agent is anything that can perceive its environment and act upon that environment.
	- the environment an agent can operate in is defined by its use case
	- the set of actions an AI agent can perform is augmented by the tools it has access to
- two aspects determine the capabilities of an agent
	- tools
	- planning
### Tools
- currently there are mainly several categories of tools 
	- knowledge augmentation
	- capability extension (=those that address the inherent limitations of AI models)
	- write actions
### Planning
#### Planning steps
1. plan generation
2. evaluate the generated plan, and generate a new one if it's a bad plan
3. execution: function calling (=invoking a tool)
4. reflection and error correction upon receiving the action outcomes
#### Things to consider during planning
- planning granularity & planning/execution trade-off
	- a detailed plan is harder to generate but easier to execute
	- a higher-level plan is easier to generate but harder to execute
- control flow (order in which actions can be executed)
	- sequential
	- parallel
	- if statement
	- for loop
	- ![Pasted image 20250308171911.png|500](/img/user/_assets/images/Pasted%20image%2020250308171911.png) (source: book AI Engineering)