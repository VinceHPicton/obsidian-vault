**Auto scaling**
Aurora can use policies, such as CPU usage, to automatically add read replicas.

**Custom endpoints**
You can define a subset of read replicas that have a specific endpoint
Typically you wont use the default read endpoint anymore once you're using these

**Serverless**
Pay per second for exactly what you use - aurora will handle bringing up and down instances according to demand - no capacity planning needed. The users talk to a "proxy fleet"

**Global aurora**
*Recommended over cross region read replicas*
- Put aurora read-only clusters in other regions to improve latency for global users, each region containing ***up to 16 read replicas per secondary region*** 
- There is one PRIMARY read-write cluster
- And also SECONDARY readonly clusters
- You can promote secondary clusters to become the primary in case of a failover

*Key fact*: typical cross-region replication in aurora takes **less than 1 second**.

**Cross region read replicas**
Simple to setup - used for disaster recovery

**Aurora ML**
ML services you can use:
- AWS sagemaker
- AWS comprehend
Dont need ML knowledge, lets ML make predictions based on your Aurora data.