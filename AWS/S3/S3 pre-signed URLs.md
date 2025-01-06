Generate a URL using any of:
- S3 console
- AWS CLI
- SDK

This URL grants the user the permissions of the AWS user which generated it.
Therefore it can be used to grant **temporary public access** to download a specific object **from a private bucket** for example, or to upload a file to a specific location on the bucket.

**The presigned URLs have a preset expiry**
- Via console: up to 12 hours
- Via CLI: max 168 hours