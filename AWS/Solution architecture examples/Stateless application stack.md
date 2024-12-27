- Route 53 for DNS
- Pointing to an ELB which operates across multiple AZs for availability
- The ELB directs to an ASG spread across multiple AZs
- Use security groups to restrict traffic to EC2 from only the ELB

![[Stateless application stack-1.png]]