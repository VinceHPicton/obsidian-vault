(NAT = Network Address Translation)
These are **EC2 instances launched in a public subnet which allow instances in a private subnet to connect to the internet by forwarding requests.**

- The NAT instance changes the source and destination IPs as it routes traffic, and for that reason **you must disable the source/destination check** on the NAT instance EC2.
- The NAT instance must also have a fixed Elastic IP attached to it.
- The VPC route tables must be configured to route traffic from the private subnets to the NAT instance.
![[NAT Instances.png|350]]

These are the **old way** and a much worse than the new way [[NAT Gateways]] because being just an EC2 in a region they aren't highly available, if the EC2 instance is small that might bottleneck your performance, you may need an ASG and resilient user-data startup script, and you have to manage security groups & rules:
- Inbound:
	- Allow HTTP/HTTPS from your private subnets
	- Allow SSH from your home network
- Outbound:
	- Allow HTTP/HTTPS to internet

