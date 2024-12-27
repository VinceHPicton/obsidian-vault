Fully managed, and serverless [[Database proxy]] for RDS and Aurora.

- It allows apps to pool and share DB connections.
- **Improves database efficiency** by reducing stress on DB resources and minimizes open connections
- It's serverless so it's autoscaling and highly available (multi-AZ)
- **Reduces failover times by 66%**
- No code changes - just point it at the proxy not the DB
- Enforce IAM authentication - like all DB proxies helps with security
- RDS proxy is never publically accessible - only accessible from within a VPC