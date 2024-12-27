By default, if no policies exist, buckets will deny access.

- User-based
	- Using IAM policies for which IAM user can access
- Resource based
	- Bucket policies (most common)
	- Object access control list (ACL) - finer grain (can be disabled)
	- Bucket ACL

An S3 object can be accessed if:
- IAM policy allows it, **OR** resource policy allows it
- There is **no explicit deny**

You can encrypt s3 objects at rest.

**S3 bucket policies**
These are the primary way of securing buckets, they're a JSON based policy, and can be used to **grant public access** ![[S3 security JSON policy.png]]
- Resources: effected buckets and objects list
- Effect: allow or deny
- Actions: which of the actions, eg get or create object to apply it to
- Principal: account or user in question

You could assign an IAM policy to an IAM user to allow bucket access, or put the policy on a role and assign it to an EC2, allowing it to add objects to the bucket.


**Bucket settings for blocking public access**
- These are set when you create a bucket, and can be changed.
- Since they're denies they override any allows. 
- If you know your bucket should never be public, leave them on.