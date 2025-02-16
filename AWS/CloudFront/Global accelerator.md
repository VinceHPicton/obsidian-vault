A service which helps you improve global application availability, performance, and security.
It **accelerates** user requests by sending them through the private AWS network.

Whereas CloudFront serves cached content, global accelerator proxies client requests to your server via the internal AWS network, for improved global performance.

Why it's faster is eg: a request is sent from Australia to your server in California, it must traverse the internet globally, making many hops between routers which adds latency and more packet failure potential. 
If instead the request goes to an AWS edge location in Australia and then over the faster private AWS network, you avoid these hops.

This is achieved through [[Anycast vs Unicast vs Multicast IP|Anycast IP]]. 

If you use global accelerator, **2 STATIC anycast IPs are assigned to your application** which route requests to the nearest edge location.
The reason there are 2 is for redundancy, either can lead a user to the same edge location depending on conditions.

You can use global accelerator with:
- Elastic IP (have traffic globally mapping to that elastic IP)
- EC2
- ALB
- NLB
All can be **public or private**

You get:
- Consistent performance globally
	- No issues with client caching an old IP, because the anycast IPs are static
- Health checks
	- Accelerator healthchecks your applications to help w failover
- Security
	- Clients only need to whitelist the 2 anycast IPs
	- DDoS protection from AWS Shield

**Vs CloudFront**
Both use edge locations + AWS Shield

CloudFront
- For caching, content is served from the edge location

Accelerator
- Proxies requests to the main services, does not directly serve requests
- Good for non-HTTP uses, eg UDP traffic, VoIP, gaming
- Good for HTTP that requires fixed IP addr

You can setup endpoints in the accelerator across many regions, and then the edge locations will forward requests to the closest endpoint to the user through the AWS network!