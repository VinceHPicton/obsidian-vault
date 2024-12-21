[[SSL & TLS|Secure sockets layer (SSL)]] certificates generally actually refer to the newer TLS certificates these days.

- These certificates include a public key for the client to encrypt a session key to be shared with the server, and public SSL (TLS) certs are issued by **certificate authorities** such as GoDaddy, and many others. 
- SSL certs have an expiration date which you must set, and must be renewed.
- The certificates can be managed via [[ACM (AWS certificate manager)]]
- The LB uses X.509 certificates, but you can also upload your own.
- On a HTTPS listener (like ALB)
	- You must specify a default certificate
	- You can use [[SNI (server name indication)|SNI]] to support multiple certs
	- You can add security policy to support older versions of SSL/TLS

**Does the load balancer just route traffic after it's done the handshake?**
*By default* yes, this is called SSL termination, what happens is the load balancer and client do the TLS handshake so they both have the session key, the LB decrypts the packets and sends the plain HTTP requests to the target groups, which is safe as long as they're in a VPC. 

This behaviour can be changed however.

 **SNI**
 [[SNI (server name indication)]] lets you have multiple SSL certs on 1 web server/load balancer
