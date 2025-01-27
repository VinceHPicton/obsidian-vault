There are 3 metrics which can be used to scale based on:
- CPU use - ECS service average CPU Utilisation
- RAM use - ECS service average memory Utilisation
- ALB request count per target.

How can you scale using these metrics?
- Target tracking - scale service in order to maintain a specific target of ALB request count/CPU/RAM use
- Step scaling - scale based on a CloudWatch alarm looking at one of the 3 above
- Scheduled scaling - scale at specific times of day etc

ECS service auto scaling is NOT the same thing as EC2 auto scaling

**EC2 launch type - method to auto scale instances**
(Fargate is serverless so dont need to worry about scaling concerns)

1. ASG scaling
Scale based on CPU utilisation within ASG itself, not in ECS

2. ECS cluster capacity provider
This is paired with an ASG and is just a **better way** to handle scaling, will handle scaling if capacity of CPU/RAM is missing