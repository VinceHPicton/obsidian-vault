- Layer 7 load balancer - meaning it can listen ONLY on HTTP or HTTPS, or websocket
- Provides a static DNS name but **NOT a static IP**
- Balance to multiple HTTP apps across many machines (target groups)
- Or balance to many apps on the **same machine**
- Support **redirects** from eg HTTP to HTTPS - this means when a client tries to connect over HTTP, they will receive a 301/302 response, redirecting them to the HTTPS resource and initiating the TLS handshake etc.
- Health checks can be only be over HTTP or HTTPS


**ALBs can route traffic to different Target Groups based on:**
- Hostname - eg www.example.com goes to 1 TG, www.another.com goes to a different one
- URL Path - eg example.com/users to 1 TG, example.com/photos to another TG
- Query Strings - eg example.com/users?platform=mobile goes to 1 and PC to another

**What can ALB route to?**
Only [[Target Groups|target groups]] which can have registered:
- EC2s
- ECS tasks
- Lambdas (HTTP req translated to JSON event)
- **Private** IP addresses (within VPC)

**Important details**
- Fixed DNS name like xxx.region.elb.amazonaws.com but IP is NOT fixed
- The servers behind the ALB do not see the client IP directly, so the ALB automatically adds the following to all requests:
	- The clients true IP is inserted into **X-Forwarded-For** header
	- The port the ALB received the request is added to **X-Forwarded-Port** 
	- The original protocol used by the client request is added to **X-Forwarded-Proto**