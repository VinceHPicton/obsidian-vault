Security group is basically the [[Firewalls|firewall]] for an EC2 instance, by default it blocks all inbound traffic, and allows all outbound. 

Security groups and EC2 instances have a many-to-many relationship:
- A security group can contain any number of EC2 instances, that's why its a group.
- An EC2 instance can be attached to any number of security groups.

Changes to a security group take effect immediately.

You can configure allowing different IPs on different port for the instance

They control what is allowed into and out of EC2 instances

Can only contain allow rules for inbound (whitelist)

All outbound traffic is allowed, all inbound traffic is blocked, by default

**Regulate access to**
- Ports
- IP ranges (v4 and v6)
- Control inbound and outbound network

Locked to a region/VPC combo

If you get infinite timeout when connecting, it’s a security group issue 100%, if you get connection refused then traffic did get through firewall.

If a request didnt get through firewall then the Ec2 would've never even known about it