If you enable S3 replication, only unencrypted objects, and those encrypted with SSE-S3 will be replicated initially. (see [[S3 replication]])
SSE-C objects can be turned on separately.

**For objects with SSE-KMS**
- You have to specify which KMS key to encrypt objects with in the replicated bucket, and make sure the KMS key policy and IAM roles allow replication
- Due to lots of use you could hit KMS throttling, in which case you'd need to request service quota increase
- You can use a multi-region key, but on replication the object will still be decrypted and then re-encrypted even though the same key was used.