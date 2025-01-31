These are [[NAT Instances]] but fully managed by AWS, so you dont have to manage many things involved with the instances.

- NATGW is created and **exists in 1 specific AZ** and uses an elastic IP
- It cannot be used by an EC2 instance in the same subnet - only by EC2s in other subnets
- You pay per hour and for bandwidth
- It requires an [[Internet Gateway]]
- 5Gb/s bandwidth, autoscaling up to 100 Gb/s
- No security groups required to manage.