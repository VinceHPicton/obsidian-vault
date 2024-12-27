AWS managed redis or memcached caching (in-memory super low latency/high perf DBs).
As it's managed, AWS takes care of OS maintenance etc. 
**Using it involves a lot of code changes for apps to actually query the cache.**

How caching works: cache hits and miss, this is called **lazy loading** - data can become stale here if some mechanism isn't deleting it.
![[Amazon Elasticache hitmiss.png]]
Another use of caching is for when a user is connecting to different instances via load balancing, their session data will be stored on the cache, so if they connect again to a new instance, they do not have to login again.
![[Elasticache user cache.png]]

![[redis vs memcached.png]]

**ElastiCache - Cache security**

- Redis supports **IAM authentication**
- Memcached supports **SASL-based**

Redis:
- You set a username/password for your redis cluster
- This is an extra level of security ontop of your security groups
- Supports SSL for in-flight

**Needed redis use case for exam** : **gaming leaderboard**
Redis **sorted sets** guarantee both uniqueness and element ordering.