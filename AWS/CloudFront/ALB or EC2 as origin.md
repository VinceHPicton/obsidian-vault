If you use an EC2:
- It **must be public** because there is no private VPC connectivity in cloudfront
- Need a security group that allows the list of public IPs of the edge locations

If you use ALB:
- The ALB must be public and allow IPs of edge locations
- The EC2s behind it can be private however