Sharding is when you split your data across multiple separate DBs.

Usually done when the DB load for **writes** is becoming impossible for 1 machine to handle, and other methods like better query optimization, better normalisation, or removing indexes etc can't solve the problem anymore. 

However sharding can also be done if the dataset becomes too large for 1 machine or to reduce contention like for DB locks.

When reads are the scaling problem you should use read replicas, better indexing or caching.

