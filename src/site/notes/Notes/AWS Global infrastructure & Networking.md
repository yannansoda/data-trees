---
{"topic":"CloudComputing","dg-publish":true,"permalink":"/Notes/AWS Global infrastructure & Networking/","dgPassFrontmatter":true,"noteIcon":""}
---

# AWS Global infrastructure 
### Determine the right region
Factors to consider when determining the right region for your services
- **compliance** with data governance and legal requirements
- **proximity** to your customers
- **available** services within a region
- **pricing** 
### Availability zone 
AWS has many data centers. Availability zone =  a single data center or a group of data centers within a Region
- Availability zones are located tens of miles apart from each other 
- Planning for failure and building a resilient and highly available architecture: run applications across at least two Availability Zones in a Region 
	- this is automatically implemented in Elastic Load Balancing, Amazon SNS, Amazon SQS
### Edge locations
An edge location = a site that **Amazon CloudFront** uses to store cached copies of your content closer to your customers for faster delivery
- AWS Edge locations run Amazon CloudFront to help get content closer to your customers, no matter where they are in the world.
- **Amazon CloudFront** is a content delivery service. It uses a network of edge locations to cache content and deliver content to customers all over the world. When content is cached, it is stored locally as a copy.


# AWS Networking
AWS networking: who should be allowed to communicate with each other.
![Pasted image 20230627145304.png|500](/img/user/assets/images/Pasted%20image%2020230627145304.png)
## Connectivity to AWS
- Amazon Virtual Private Cloud (Amazon VPC)
	- = A networking service that you can use to establish boundaries around your AWS resources 
- Subnet
	- = a section of a VPC in which you can group resources based on security or operational need
	- can be private or public
	- Within a virtual private cloud (VPC), you can organize your resources into subnets
- Internet gateway
	- = a connection between a VPC and the internet.
	- To allow public traffic from the internet to access your VPC, you attach an internet gateway to the VPC.
- Virtual private gateway
	- =  the component that allows protected internet traffic to enter into the VPC
	- A virtual private gateway enables you to establish a virtual private network (VPN) connection between your VPC and a private network, such as an on-premises data center or internal corporate network.  
	- can be achieved by AWS Direct Connect -> establish a private dedicated connection 

## Network traffic in a VPC
- packet
	- A packet = a unit of data sent over the internet or a network.
	- When a customer requests data from an application hosted in the AWS Cloud, this request is sent as a packet.
	- Before a packet can enter into a subnet or exit from a subnet, it checks for permissions. 
- Network access control lists (ACLs)
	- The VPC component that checks packet permissions for subnets is an ACL.
	- ACL = a virtual firewall that controls inbound and outbound traffic at the subnet level.
	- By default, a security group allows all inbound traffic and allows all outbound traffic.
	- Network ACLs perform stateless packet filtering. They remember nothing and check packets that cross the subnet border each way: inbound and outbound. 
- Security groups
	- The VPC component that checks packet permissions for an Amazon EC2 instance is a security group.
	- A security group = a virtual firewall that controls inbound and outbound traffic for an Amazon EC2 instance.
	- By default, a security group denies all inbound traffic and allows all outbound traffic.
	- Security groups perform stateful packet filtering. They remember previous decisions made for incoming packets.

## Global Networking
- Domain Name System (DNS) ![Pasted image 20230628160452.png|500](/img/user/assets/images/Pasted%20image%2020230628160452.png)
	- DNS is like the phone book of the internet; it is a directory used for matching domain names to IP addresses.
	- DNS resolution: the process of translating a domain name to an IP address. 
	- AWS DNS web service: Amazon Route 53 
		-  manage the DNS records for domain names
>[!Example] Amazon Route 53 and Amazon CloudFront deliver content together ![Pasted image 20230628160825.png|500](/img/user/assets/images/Pasted%20image%2020230628160825.png)
>Suppose that AnyCompany’s application is running on several Amazon EC2 instances. These instances are in an Auto Scaling group that attaches to an Application Load Balancer. 
>1. A customer requests data from the application by going to AnyCompany’s website. 
>2. Amazon Route 53 uses DNS resolution to identify AnyCompany.com’s corresponding IP address, 192.0.2.0. This information is sent back to the customer. 
>3. The customer’s request is sent to the nearest edge location through Amazon CloudFront. 
>4. Amazon CloudFront connects to the Application Load Balancer, which sends the incoming packet to an Amazon EC2 instance.






