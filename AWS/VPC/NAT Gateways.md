Are used to enable instances in a **private subnet** to access the internet while preventing unsolicited inbound traffic from the internet. This means external services outside the VPC cannot initiate a connection with those instances.

They are [[NAT Instances]] but fully managed by AWS, so you dont have to manage many things involved with the instances.

- NATGW is created and **exists in 1 specific AZ** and uses an elastic IP
- It cannot be used by an EC2 instance in the same subnet - only by EC2s in other subnets
- You pay per hour and for bandwidth
- It requires an [[Internet Gateway]]
- 5Gb/s bandwidth, autoscaling up to 100 Gb/s
- No security groups required to manage.
![[NAT Gateways2.png]]

**Availability**
NAT gateways are resilient within their AZ, but will go down if the AZ goes down. Obviously there is no cross-AZ failover because if the AZ is down the EC2s in it are also down.

Therefore you must create multiple NAT gateways in multiple AZs to achieve fault tolerance.

![[NAT Gateways3.png|400]]