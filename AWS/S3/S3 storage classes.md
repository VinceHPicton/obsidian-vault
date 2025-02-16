All storage in S3 has 99.9999999& durability, (11 9s)
You can manually move between classes, or use S3 lifecycle configurations (rules for the bucket that say when objects should be moved)

*General purpose tiers:*
***
**Standard**
No minimum storage duration
Used for frequently accessed objects, low latency, high throughput, can sustain 2 concurrent AZ failures

**Standard IA (infrequent access)**
Minimum storage duration 30 days
Has an access cost, but lower storage cost

**One Zone IA**
Minimum storage duration 30 days
Data lost if AZ is destroyed, but cheaper

*What does minimum storage duration mean?*
It means you will be charged as if the object was stored that long even if deleted before.

*Glacier tiers:*
***
**Glacier Instant retrieval**
Minimum storage duration 90 days
Millisecond retrieval

**Glacier Flexible retrieval**
Minimum storage duration 90 days
3 modes of retrieval:
- Expedited (1-5 mins retrieval)
- Standard (3-5 hours retrieval)
- Bulk (5-12 hours retrieval) but this is free!

**Glacier Deep Archive**
Minimum storage duration 180 days
2 modes of retrieval:
- Standard - 12 hours retrieval
- Bulk - 48 hours retrieval

**Intelligent Tiering**
Minimum storage duration 30 days
Incurs a small monthly monitoring fee
No retrieval charges

When intelligent tiering will choose storage tiers:
1. Frequent access - default location for objects
2. Infrequent access - if an object is not accessed for 30 days
3. Archive IA - if an object is not accessed for 90 days
4. Archive Access - configurable 90-700 days
5. Deep Archive access - configurable 180-700+ days


