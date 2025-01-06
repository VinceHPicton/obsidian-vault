You can achieve:
- 3500 PUT/COPY/POST/DELETE
- or 5500 GET/HEAD 
Requests **per second per prefix** in a bucket

**What's a prefix?**
bucketname/folder1/sub1/filename.txt => prefix: /folder1/sub1
So if you had 5 prefixes, you can achieve 5x requests in the bucket.

**Multi-part upload**
- Recommended for files > 100MB
- Required for files > 5GB
- Parallelizes uploads, so speeds them up.

**S3 Transfer Acceleration**
Increase transfer speed by uploading file to an edge location, and having that forward it to the target region.
Can use it with multi-part upload.
Uses the fast private AWS network so thats why faster.

**Byte-range fetches**
Parallelize GET by requesting specific byte ranges
This means better resilience in case of a failure.
Can be used to request only part of a file if needed.