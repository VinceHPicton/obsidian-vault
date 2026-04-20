
Memcached is deliberately minimal, it's optimized for pure speed, so if you just want a very simple cache, like caching blobs of data from a DB. use memcached.


Redis has a much richer API and feature set, and can act as a cache and a lightweight DB, but therefore comes with more complexity.


Another point is about persistance.
If cache loss is acceptable either is fine, but if your cache needs durability, redis is your only option.