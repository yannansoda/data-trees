---
{"topic":"DataScience, CloudComputing","dg-publish":true,"permalink":"/Notes/Amazon EC2/","dgPassFrontmatter":true,"noteIcon":""}
---

## What is Amazon EC2
EC2 = Amazon Elastic Compute Cloud 

## Key steps Amazon EC2
1. choose **EC2 instance type**
2. scale EC2 instances either vertically by resizing the instance, or horizontally by launching new instances and adding them to the pool. You can set up automated horizontal scaling, using Amazon **EC2 Auto Scaling**. 
3. Once the EC2 instances is scaled out horizontally, we need distribute the incoming traffic across those instances. This is where the **Elastic Load Balancer** comes into play. 
4. know different **pricing models**. 

## How does EC2 work
1. launch
2. connect
3. use
## Amazon EC2 instance types
 When you launch an EC2 instance, you choose the instance family.
>[!Note] An instance = A copy of an Amazon Machine Image (AMI) running as a virtual server in the AWS Cloud.
- General purpose instances
	- provide a balance of compute, memory, and networking resources.
- Compute optimized instances
	- ideal for compute-bound applications that benefit from high-performance processors. 
	- use cases: batch processing
- Memory optimized instances
	- designed to deliver fast performance for workloads that process large datasets in memory.
	- use cases: high-performance databases
- Accelerated computing instances
	- for hardware accelerators, or coprocessors, to perform some functions more efficiently than is possible in software running on CPUs.
- Storage optimized instances 
	- designed for workloads that require high, sequential read and write access to large datasets on local storage. 
	- use cases: distributed file systems, data warehousing applications, and high-frequency online transaction processing (OLTP) systems.

## Scalability & Elasticity
## Scalability 
- Scalability involves beginning with only the resources you need and designing your architecture to automatically respond to changing demand by scaling out or in. 
- can be achieved by **Amazon EC2 Auto Scaling**
	- dynamic scaling: responds to changing demand
	- predictive scaling: automatically schedules the right number of Amazon EC2 instances based on predicted demand
![Pasted image 20230622153307.png|200](/img/user/assets/images/Pasted%20image%2020230622153307.png)
## Elasticity
- can be achieved by **Elastic Load Balancing** = the AWS service that automatically distributes incoming application traffic across multiple resources, such as Amazon EC2 instances. 
	- low-demand period: ![Pasted image 20230622154505.png|300](/img/user/assets/images/Pasted%20image%2020230622154505.png)
	- high-demand period: ![Pasted image 20230622154600.png|300](/img/user/assets/images/Pasted%20image%2020230622154600.png)

## Amazon EC2 pricing
- On-Demand
	- deal for short-term, irregular workloads that cannot be interrupted.
- Amazon EC2 Saving Plans
	- reduce your compute costs by committing to a consistent amount of compute usage for a 1-year or 3-year term. 
	- offer you cost savings at up to 72% off of On-Demand prices.
- Reserved Instance
	- a billing discount applied to the use of On-Demand Instances
	-  require a commitment of either 1 year or 3 years
- Spot Instances
	- ideal for workloads with flexible start and end times, or that can withstand interruptions. 
	- offer you cost savings at up to 90% off of On-Demand prices.
- Dedicated Hosts
	- physical servers with Amazon EC2 instance capacity that is fully dedicated to your use. 
	- higher cost than others



