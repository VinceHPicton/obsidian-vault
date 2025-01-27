*Elastic container service*

When you run a container on ECS, it will run within a **task** which is within a **cluster**.
A **service** is a group of ECS tasks that are meant to stay online, eg a web server.
A **single task** is more likely to be something that spins up and runs, then dies.

There are 2 launch types: EC2 and Fargate:
**EC2 launch type**
- You provision the underlying EC2s
- Each EC2 runs the "ECS agent"
- AWS stops and starts containers as needed

**Fargate**
- Serverless version
- All you create is a task definition and AWS does the rest


**IAM roles on ECS**
EC2 instance profile:
The ECS container agent (software running on the EC2) needs permissions to interact with other AWS services like ECR, Secrets manager, CloudWatch for logs. The Instance profile provides these permissions through its IAM role.

EC2 Task roles
- Allow specific tasks to access other services, eg S3


**ECS and Load Balancers**
You can use [[Application load balancer (ALB)|ALB]] to load balance requests between ECS tasks, [[Network load balancer (NLB)|NLB]] can also be used but only recommended for high throughput uses.

**ECS and Data Volumes**
Important use case is with [[EFS (elastic file system)|EFS]]. You can mount an EFS to many different tasks so they share the same data.
![[ECS.png]]