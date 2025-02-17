Elasticache is an AWS service which provides [[caching]] for your databases.
Caching is used to take load off your **databases** by caching query results. 

- Elasticache allows you to use either **redis** which is more powerful but complex, or **memcached** which is simpler.
- As it's managed, AWS takes care of OS maintenance etc. 
- Important to remember that is is for database caching

**MOST IMPORTANT EXAM FACT: Using it involves a lot of CODE CHANGES for apps to actually query the cache.**
Therefore if exam says "without code changes" it's not elasticache

**How caching works**
Database queries can result in a hit or miss, this is called **lazy loading** - data can become stale here if some mechanism isn't deleting it.
- If there is a hit, the database doesn't need to process the query, as the cache returns it.
- If there is a miss, the cache does not have the result, the DB is queries and then Elasticache stores the result for future use.
![[Amazon Elasticache hitmiss.png]]
Another use of caching is for when a user is connecting to different instances via load balancing, their **session data** will be stored on the cache, so if they connect again to a new instance, they do not have to login again.
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