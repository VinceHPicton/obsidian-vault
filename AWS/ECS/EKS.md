Elastic kubernetes service

- Allows you to launch mamaged K8s clusters on AWS
- It's an alternative to ECS but open source and a different API
- Use case is for **cloud-agnostic** customers
- Supports:
	- EC2 if you want to deploy worker nodes
	- Fargate if you want serverless containers.

**EKS Node types**
A node = an EC2 instance running container(s)
Pods are an abstraction of containers, basically like tasks in ECS

1. *Managed Node groups*
- On-Demand or spot instances
- The nodes are part of an ASG which is managed by EKS
- The nodes are created and managed for you.

2. *Self-managed nodes*
- On-Demand or spot instances
- You create the nodes and register them to the EKS cluster, they are managed by ASG
- There is a premade AMI from amazon: Amazon EKS optimized AMI

3. *AWS Fargate*
- No nodes to manage at all - it's all serverless.


**EKS Data volumes**
If you want persistent data volumes (optional)

This uses a CSI (container storage interface) compliance driver.

Supports:
- [[EBS]]
- [[EFS (elastic file system)]] - the ONLY option for Fargate
- [[Amazon FSx]] For Lustre
- FSx for NatApp ONTAP