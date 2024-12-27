All storage in S3 has 99.9999999& durability, (11 9s)

*General purpose tiers:*
***
**Standard**
Used for frequently accessed objects, low latency, high throughput, can sustain 2 concurrent AZ failures

**Standard IA (infrequent access)**
Has an access cost, but lower storage cost

**One Zone IA**
Data lost if AZ is destroyed, but cheaper


*Glacier tiers:*
***
**Glacier Instant retrieval**
Millisecond retrieval

**Glacier Flexible retrieval**
3 modes of retrieval:
- Expedited (1-5 mins)
- Standard (3-5 hours)
- Bulk (5-12 hours) but this is free!

**Glacier Deep Archive**
- Standard - 12 hours
- Bulk 48 hours

**Intelligent Tiering**
Incurs a small monthly monitoring fee
No retrieval charge

Tiers:
1. Frequent access - default
2. Infrequent access - not accessed for 30 days
3. Archive IA - 90 days
4. Archive Access - configurable 90-700 days
5. Deep Archive access - config 180-700+ days

*You can manually move between classes, or use S3 lifecycle configurations*
