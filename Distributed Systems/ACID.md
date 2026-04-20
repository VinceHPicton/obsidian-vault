ACID = Atomicity, Consistency, Isolation, Durability

ACID is most often referring to a type of database, and an ACID system means validity of data is guaranteed at all costs over availability. So if any part of a DB transaction fails, the whole transaction fails.

This means in the case of crashes, network failure, etc, the data will always remain valid (eg half a transaction wouldn't be able to happen), but **the trade-off is the system is not as available** as a [[BASE]] type database. 

SQL databases tend to be ACID