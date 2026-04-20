

## **Write-through**
New writes go to both the cache and DB immediately.
Cache is always warm, but adds write latency, and also wasted writes to cache for unused data



## **Write-around**
Writes go directly to DB, not the cache.



## **Write-back (write-behind)**
Writes to cache FIRST, the DB is updated later.
Risk of data loss if cache crashes