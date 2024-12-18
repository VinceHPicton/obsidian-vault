Managed load balancer which operates within 1 **region** only - can distribute load to any AZ within that region.
It costs less to setup your own LB but it would be a nightmare.

**Why use a load balancer?**
- Exposes a single point of access (IP) for an app with multiple instances
- Seamlessly handle any instance failures
- Spread load across instances
- Health check instances regularly to alert for failures
- Provide HTTPS
- High availability across zones

**Health checks**
Request sent periodically to usually /health.
If 200 OK not received the ELB wont forward traffic to that instance.