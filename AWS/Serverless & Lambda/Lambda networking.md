By default, lambdas are launched in an AWS VPC, not in your own one, this means they cannot access resources inside your VPC, unless you define your VPC ID in the lambda subnets and SGs.


![[Lambda networking.png|400]]
(DynamoDB is a public resource on AWS cloud, so Lambda can access it by default)


**A key use case: Lambda + [[RDS Proxy]]**
RDS Proxy is **NEVER** publicly accessible, so the Lambdas using it must be deployed into your VPC.
You would use this pattern to reduce strain on DB through lambdas opening and closing too many connections.
![[Lambda networking 1.png]]