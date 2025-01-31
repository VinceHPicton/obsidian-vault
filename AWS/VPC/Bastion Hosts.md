Basically they are an EC2 in a public subnet that can connect to EC2s in a private subnet within the VPC, they can be used to SSH into the private subnet EC2s

The Bastion host security group must allow inbound traffic on port 22 **from a restricted CIDR** like your company CIDR
The security group of the private EC2s must allow either the security group of the bastion host or the **private IP** of the bastion host.
![[Bastion Hosts.png]]
