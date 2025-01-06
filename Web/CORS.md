Cross-origin resource sharing is a mechanism browsers use to allow/deny request to a different origin than the one currently being visited (let's call this the main origin).

An origin is defined by a combination of the protocol, domain, and port.
Eg https://www.example.com (https implies port 443)

If something from the main origin wants the browser to send a request to a different origin, the browser first makes a **preflight request** (A HTTP OPTIONS request) to the different origin, which includes the main origin - essentially asking the different origin if it allows requests from the main origin. 

The different origin replies with a **preflight response** which can:

**Deny the main origin request**
If this happens (by either not including the necessary headers or specifying that the main origin is not allowed), the browser will block the actual request. In this case, the browser will display a CORS error in the developer console, indicating that the request was blocked due to the absence of a valid CORS policy.

**Allow the request**
If this happens the different origin will provide headers:
- Access-Control-Allow-Origin: www.mainorigin.com
- Access-Control-Allow-Methods: GET, PUT, DELETE (The allowed methods)
- `Access-Control-Allow-Headers: Content-Type, Authorization` (The allowed custom headers that can be sent to different origin)

If it replies with these headers, the browser will allow requests to the different origin.

Subsequent requests may or may not trigger a new preflight request, it depends on factoring like caching and a `Access-Control-Max-Age: 3600` (seconds) header which may be sent with the preflight response.