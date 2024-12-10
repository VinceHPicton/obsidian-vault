Security group is basically a virtual [[Firewalls|firewall]] for an EC2 instance, by default it blocks all inbound traffic, and allows all outbound. 

In AWS it acts as a set of rules defining inbound and outbound allowed traffic to the instance.

**Key facts for exam**
- Security groups and EC2 instances have a many-to-many relationship:
	- A security group be attached to any number of EC2 instances, that's why its a group.
	- An EC2 instance can be attached to any number of security groups.
- Changes to a security group take effect **immediately**.
- **By default**
	- All outbound traffic is allowed
	- All inbound traffic is blocked
- Security groups exist within a **region** and cant be used outside it
- Security groups live "outside" the EC2, traffic blocked by the SG is never seen by the instance.
- Application timeout is a security group issue
- Connection refused is **not** a SG issue, the app rejected request

**SGs regulate access to**
- Ports
- IP ranges (v4 and v6)
- Control inbound and outbound network

You can configure allowing different IPs on different port for the instance

It's best practice to create a separate SG for SSH access to instances