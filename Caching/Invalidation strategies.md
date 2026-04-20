# TTL (time to live)
- Extremely simple: data is invalid after 60s
- You **will** at times serve invalid data
- Suitable where eventual consistency is fine

# Event-based
When data changes, invalidate/update cache.
Can also use pub/sub system to trigger cache invalidation


Write-through and write-behind [[Cache write strategies]] also effectively handle cache invalidation


### In practice, many different strategies are used at once, eg various events + a TTL as a failsafe