Edge function = some code you write and attach to your [[CloudFront]] CDN which runs close to users to minimize latency.
These functions are run fully serverlessly.

A few use cases: A/B testing, Bot mitigation, Authentication.

**CloudFront functions**
- Super lightweight, high performance, high scale, can only impact viewer request and response types (see diagram).
- Only JavaScript, very quick and simple functions.
- **Max execution time less than 1 ms!**
- **Millions** of request per second
*Use cases* 
- Cache key normalization
- Header manipulation (eg HTTP headers)
- URL rewrites/redirects
- Token validation eg JWT

**Lambda@Edge**
- Much larger functions, can effect **origin** request/response **AND** **viewer** request/response
- **Max execution 5-10 seconds.**
- **Thousands** of requests per second
- These are lambda functions can be in Node.js or python.
- Requests are written in on AWS region and replicated to the edge locations
![[Lambda@Edge and CloudFront functions.png]]