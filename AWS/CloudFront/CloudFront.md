CloudFront is AWS' [[CDN]] 

**CloudFront distributions** can only be **changed (configured)** in the **us-east-1 (N. Virginia) region**, but they work globally.

Like all CDNs it's used to improve latency by caching content at the 216 aws global points of presence.
CloudFront integrates with Shield, giving DDoS protection.

**Available origin types**

**S3 bucket**
- CloudFront can also be used as ingress for your S3 bucket (for uploads)
- Security is enhanced through **Origin Access Control** (OAC), which is replacing OAI (origin access identity)
- On top of securitty provided through the S3 bucket policy

**Any custom origin using an HTTP backend**
- Application load balancer
- EC2 instance
- S3 website
- Any HTTP backend you want


**CloudFront vs S3 cross region replicas**
CloudFront
- is a global edge network (not just regions)
- not readonly
- Files cached for a TTL (normally a day)
- Great for **static content** that must be **globally available**

S3 replicas
- readonly
- Must be set up for each specific region yourself
- Files updated almost real-time, unlike CloudFront which may take a day due to TTL
- Great for **dynamic content** needed in a **few regions** with low-latency