---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/Notes/ML System Monitoring and Continual learning/","dgPassFrontmatter":true,"noteIcon":""}
---

# Causes of ML System Failures
### Software system failures
- dependency failure
- deployment failure
- hardware failure
- downtime/crashing
### ML-Specific Failures
- data distribution shifts: [[Notes/Machine Learning All-in-one#^8a1aad\|Machine Learning All-in-one#^8a1aad]]
- edge cases
>[!Quote] Designing Machine Learning Systems
>**Edge cases vs. Outliers**
>- Outliers refer to data: an example that differs significantly from other examples. Edge cases refer to performance: an example where a model performs significantly worse than other examples. 
>- An outlier can cause a model to perform unusually poorly, which makes it an edge case. However, not all outliers are edge cases. For example, a person jaywalking on a highway is an outlier, but it’s not an edge case if your self-driving car can accurately detect that person and decide on a motion response appropriately.
- degenerate feedback loops
	- created when a system’s outputs are used to generate the system’s future inputs, which, in turn, influence the system’s future outputs.
	- especially common in tasks with natural labels from users, such as recommender systems and ads click-through-rate prediction: “exposure bias", “popularity bias”, “filter bubbles”

# Monitoring & Observability
## Monitoring 
= the act of tracking, measuring, and logging different metrics that can help us determine when something goes wrong
### Metrics
- operational metrics: the metrics that should be monitored with any software systems such as 
	- latency
	- throughput
	- CPU utilization
	- server load
- input metrics
	- average input length
	- average input volume
	- number of missing values
	- average image brightness
- output metrics
	- times return Null
	- times user redoes search
	- times user switches to typing 
- ML-specific metrics
	- monitoring accuracy-related metrics
	- monitoring predictions
	- monitoring features
	- monitoring raw inputs
>[!Tips]
> Always think about how quickly do metrics change in your data!
> For example, user data generally change slowly, but B2B data can change really fast!
### Monitoring toolbox
- logs
- dashboards
- alerts
### Performance auditing
- How to evaluate model's performance even before it's deployed: [[Notes/Model Offline Evaluation\|Model Offline Evaluation]]
- When performance is unexpected:
	1. brainstorm the ways the system might go wrong
	2. establish metrics to assess performance against these issues on *appropriate slices of data* using [[Notes/Error analysis\|Error analysis]]
## Observability 
= setting up our system in a way that gives us visibility into our system to help us investigate what went wrong


# Continual Learning

### Types of model updates
- model iteration
= A new feature is added to an existing model architecture or the model architecture is changed.
- data iteration
= The model architecture and features remain the same, but you refresh this model with new data

>[!Link]
>The two types can be also regarded as [[Model-centric vs. Data-centric AI Development\|Model-centric vs. Data-centric AI Development]]
>
### Stateful retraining vs. Stateless retraining 
![Pasted image 20230714115417.png|400](/img/user/assets/images/Pasted%20image%2020230714115417.png)
- stateful retraining (fine-tuning/incremental learning)
	- the model continues training on new data
	- mostly applied for data iteration
- stateless retraining
	- the model is trained from scratch each time

### Four Stages of Continual Learning
1. Stage 1 - Manual, stateless retraining
2. Stage 2 - Automated retraining: needs infrastructure
3. Stage 3 - Automated, stateful training: needs set fixed model updating schedule
4. Stage 4 - Continual learning: model will be updated automatically with triggers:
	- time-based
	- performance-based
	- volume-based
	- drift-based

# Test in Production
There are several techniques for evaluating the model in production
### Blue/Green
![Pasted image 20231004151507.png|500](/img/user/assets/images/Pasted%20image%2020231004151507.png)
- derived from software development
- shift all traffic to the new model by updating Load Balancer
### Shadow deployment /Challenger (challenger model)  ![Pasted image 20231004151652.png|500](/img/user/assets/images/Pasted%20image%2020231004151652.png)
1. Deploy the candidate model in parallel with the existing model.
2. For each incoming request, route it to both models to make predictions, but only serve the existing model’s prediction to the user.
3. Log the predictions from the new model for analysis purposes
4. Replace the existing model with the new model if the new model's predictions are satisfactory
### A/B testing ([[Notes/AB testing\|AB testing]]) 

![Pasted image 20231004151346.png|500](/img/user/assets/images/Pasted%20image%2020231004151346.png)
1. Deploy the candidate model alongside the existing model.
2. A percentage of traffic is routed to the new model for predictions; the rest is routed to the existing model for predictions.
3. Monitor and analyze the predictions and user feedback, and do stats test if any difference in prediction within long validation cycles
### Canary release 

![Pasted image 20231004151716.png|500](/img/user/assets/images/Pasted%20image%2020231004151716.png)
1. Deploy the candidate model alongside the existing model. The candidate model is called the canary.
2. A portion of the traffic is routed to the candidate model.
3. If its performance is satisfactory, increase the traffic to the candidate model. If not, abort the canary and route all the traffic back to the existing model.
4. Stop when either the canary serves all the traffic (the candidate model has replaced the existing model) or when the canary is aborted.
### Interleaving experiments
### Multi-Armed Bandits ![Pasted image 20231004151936.png|600](/img/user/assets/images/Pasted%20image%2020231004151936.png)
- different other static approaches, it is a dynamic approach = it tests model versions using reinforcement learning
- exploit & explore
