A bucket can only have 1 default encryption key, but on upload you can specify a different key for an individual object.
SSE-S3 is automatically applied to new objects.
You can force an encryption type with a bucket policy 
**Bucket policies are evaluated before default encryption** so they can override the default.

There are 4 methods of encryption in S3, split across 2 categories:

(SSE = server-side encryption):
- SSE-S3 - keys owned and managed by AWS on the S3 service
- SSE-KMS - keys handled by you via the AWS KMS service
- SSE-C - keys are fully managed by customer, outside of AWS
- Client-side encryption - data is encrypted before sending it to AWS

**SSE-S3**
- **AES-256** encryption
- Header: **"x-amz-server-side-encryption" : "AES256"**
- The **default** for new buckets and objects

**SSE-KMS**
- You get to control the keys
- Header: **"x-amz-server-side-encryption" : "aws:kms"**
- Limitation: the KMS limits
	- On upload: s3 calls **GenerateKeyData** KMS API
	- On download: s3 calls **Decrypt** KMS API
	- This counts to the KMS quota per second so you may be rate-limited by this
	- You can request quote increase via Service Quotas Console.

**SSE-C**
- S3 does NOT store the key, the **client sends it with the data**
- Therefore you're **required to use HTTPS** (else you're sending your key across the web)
- Key provided in **HTTP headers** for every request made

**Client-side encryption**
- Use client libraries like **Amazon S3 client-side encryption library**

**Encryption in transit (SSL/TLS)**
Amazon S3 exposes 2 endpoints: a HTTP and a HTTPS one.
Obviously, HTTPS is recommended, and required for SSE-C.

**You can also force encryption in transit for a bucket with a bucket policy.**