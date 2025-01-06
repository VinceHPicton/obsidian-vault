These allow you to simplify your access policies by providing separate DNS name access to different prefixes (remember these are basically folders) within an S3 bucket.

An access point has:
- A DNS name
- An access point policy

You could grant read-only policy for analytics users using the analytics access point.
Read-write access to finance users but only for the finance endpoint. etc.

![[S3 Access Points img.png]]

**Access points within a VPC**
Provide a private access point for devices only within the bucket VPC - not exposed to the internet.

- You need to create a VPC endpoint
- The VPC endpoint policy must grant access to the bucket and also the access policy.

![[S3 Access Points VPC.png]]