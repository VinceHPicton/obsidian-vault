Access logs allow you to log any action that happens to a bucket, whether it was authorized (successful) or not.

The logs must be placed in a separate bucket to avoid an infinite logging loop - where a log is made that a log was made to the bucket, and so on.

The logging target must be in the **same region** as the bucket.