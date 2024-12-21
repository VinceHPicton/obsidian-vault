An ASG is an AWS resource which manages a group of EC2 instances, you set a minimum, maximum, and desired number of instances that the ASG should always have. The purpose is to scale out or in depending on load, saving money while matching unpredictable traffic.

If EC2s fail healthchecks, bringing the ASG below the "desired" number, the ASG will spin up new instances to get back the desired number.

The ASG guarantees the minimum number EC2s will always exist, the number may fall below the desired but not the minimum.

ASG are **free** you only pay for the EC2s underlying it.

ASGs can be closely associated with a LB via a target group as explained [[ASG, EC2, ELB, Target group concept|here]]

**ASG attributes**
- launch template - this defines what the EC2s in the ASG look like
	- Instance type eg t2.micro
	- AMI
	- EBS volumes
	- Security groups
	- User data (startup script)
	- many more
- Minimum/max/desired
- Scaling policies

The ASG can use a variety of metrics, such as **cloudwatch alarms** as scale out/scale in policies, which determine when it will create/destroy instances.