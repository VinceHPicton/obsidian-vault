- For this we start with a [[Stateless application stack]] but now we will want to add:
- RDS spread across multiple AZs using multi-AZ for availability
- Read replicas if there are read heavy workloads
- Redis or Elasticache to preserve session for users across different EC2 - like shopping cart - Redis can be multi-AZ
- Use security groups to restrict traffic to EC2 from only the ELB, and for the DBs for only traffic from the EC2 SGs
- This is a typical **3 tier architecture** within 1 region - we have the public subnet (ELB), private subnet (EC2s), and the data subnet (caches and RDS)
![[Stateful application stack.png]]