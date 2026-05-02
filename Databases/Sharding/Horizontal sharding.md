Horizontal sharding involves splitting **rows** within the same table across databases, whereas [[Vertical sharding]] involves splitting columns or features into different databases, eg user profile vs transactions.

You need to choose your sharding strategy in such a way that it spreads load evenly between your shards
# Sharding strategies
### Hash-based
Use a hash function on eg user_id to lead to a specific shard.
This results in an even distribution, but it can be difficult to add new shards later - may require downtime while data is redistributed and hash function would need to be changed.

### Range-based
eg user_id 1-1000000 = shard 1
1000001-2000000 = shard 2
Need to choose your ranging method carefully or you can end up with uneven lead across shards.

### Directory-based (lookup service)
In this strategy you store a directory of where each user's shard is, at the cost of adding the extra hop to this lookup service on a request.
You can add more shards easily, and rebalance your shards easily, but the lookup service can become a dangerous single point of failure

### Geo sharding
Split DB by eg country