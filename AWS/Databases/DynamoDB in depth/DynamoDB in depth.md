https://www.youtube.com/watch?v=HaEPXoXVf2k

Why use NoSQL?
Relational DBs were invented to reduce the disk space required for data, back decades ago when storage space was very expensive, they normalise the data into tables.
RDBs come with high CPU cost however, to make joins etc happen which puts the data back together.
Today CPU cost is far higher than for storage, so why keep using a technology optimised for low storage space? Instead use one which optimizes for compute power.

**What does a table in DynamoDB look like?**
![[DynamoDB table.png]]

In dynamoDB each table represents a unique logical keyspace, this is the way **all NoSQL databases work**. 

We essentially hash the items unique ID to produce the **partition key** so we can place the items in an order along the logical key space of partition keys.

![[DynamoDB logical keyspace.png]]

When we scale this DB up we can just chop the keyspace up and assign different partitions of it to different physical storage devices

![[DynamoDB scaled keyspace.png]]

When this partitioning has happened, items in the same storage device also get a **sort key** so that each item can be uniquely identified within the keyspace under it's **partition key + sort key** so that infinite items can exist within a partition - they will hash to the same partition key as same ID, but have different sort keys so can still be uniquely identified.

![[DynamoDB infinite partitions.png]]

We want data to be evenly and randomly distributed across the keyspace, so that you don't have 1 node taking all the load because it has a "hot" part of the keyspace:
![[DynamoDB video heatmap.png]]

Dynamo auto-adapts it's throughput capabilty to your actual traffic
![[DynamoDB video autoscaling.png]]

The data is still always going to be relational, so how do we handle relations in NoSQL

**DynamoDB key concepts**
Selecting a good partition and sort key is core to the efficiency

Partition key:
- Large number of distinct values
- Items are uniformly requested (across the key space) and randomly distributed
- Good examples: CustomerID, DeviceID. Terrible examples: status, gender

Sort keys:
- Able to model 1:n and n:n relations
- Efficient selective patterns
- Able to leverage range queries
- Examples: Orders and OrderItems

Types of apps with NoSQL:
- OLAP does not fit with a NoSQL backend
- OLTP/DSS do

It's important to model data for 1 service using 1 table!
Don't use relational DB patterns for NoSQL databases


Maintaining version history pattern: 
If there's a new version of something, overwrite a "v0" item and add the item under vX
![[DynamoDB in depth versioning.png]]

Hierarchical data structures as items, using composite keys:
![[DynamoDB in depth.png]]

You can seach for, for example, all offices in NY with partition key = USA, and the sort key start with NY..., new york city with starts with: NY#NYC...


Conclusions
- NoSQL does NOT mean used for non relational data - **all data is relational**
- The entity relationship diagram (ERD) still matters
- RDBMS is not [[Deprecated|deprecated]] by NoSQL - they have different uses
- Use NoSQL for [[OLTP]] or DSS at scale
- Use RDBMS for OLAP, or OLTP when scale is not important