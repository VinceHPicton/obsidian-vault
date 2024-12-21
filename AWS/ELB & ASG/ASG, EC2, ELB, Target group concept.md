Target groups are just a group of Ec2 instances. Target groups are closely associated with ELB and not ASG.

- ELB -> TG - > Group of Instances

We can just use ELB and Target groups to route requests to EC2 instances. With this setup, there is no autoscaling which means instances cannot be added or removed when your load increases/decreases.

- ELB -> TG - > ASG -> Group of Instances

If you want autoscaling, you can attach a TG to ASG which in turn gets associated to ELB. Now with this setup, you get request routing and autoscaling together. Real world usecases follow this pattern. If you detach the target group from the Auto Scaling group, the instances are automatically deregistered from the target group

