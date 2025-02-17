If not using caching like cloudfront outside your VPC, you can use the NACL, as NACL can have deny rules, whereas security groups **cannot** - they only have allow.

The [[8. WAF]] is also a way to control specific IPs - and can be used on cloudfront, however it is a layer 7 blocker so cannot be used with network load balancer, only with ALB.

It's also possible to install some firewall software on the Ec2, but then there is still compute done for blocked requests.

Using any load balancer, you can use NACL obviously, as they are inside the VPC.