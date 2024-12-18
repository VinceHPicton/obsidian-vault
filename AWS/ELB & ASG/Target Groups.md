Target groups are groups of AWS services of a specific type which are routed traffic from a load balancer:
- EC2 instances (which can be managed by an auto scaling group)- HTTP
- ECS tasks (managed by ECS itself) - HTTP
- Lambda functions - HTTP request is translated into JSON event
- IP addresses - must be private IPs
- Application Load balancers


