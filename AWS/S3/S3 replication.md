You can do cross region replication (CRR) or same region replication (SRR)

- You must **enable versioning** in both the source and destination
- Buckets can be in different accounts
- Copying is asynchronous
- Must give the buckets proper IAM permissions

**Uses**
- CRR: compliance, low latency, replication across accounts
- SRR: log aggregation, live replications between prod and test.

When you enable replication, **only new objects are replicated.**
To do old objects you'd have to do a batch replication (this can be done at the time you enable replication).

**No replication "chaining"**
Meaning if bucket A objects are replicated into bucket B, and bucket B into bucket C, then the objects from A are not duplicated twice into bucket C.

**Deletes and replication**
Delete markers are not replicated by default, but you can turn this on in your replication rule.

If you delete a specific version in the source bucket, that change wont be replicated, because only delete *markers* are replicated, not deletes.