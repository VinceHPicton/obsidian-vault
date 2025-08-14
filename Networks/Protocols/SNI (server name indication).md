SNI is part of the TLS handshake which solves the problem of a load balancer (or any server hosting multiple domains) hosting multiple domains without each domain having to have a unique public IP, eg "www.mywebsite.com" and also "www.secondarysite.com" from 1 LB/server

Without SNI:
- A connection comes to the server from the internet, intending to connect to "www.mywebsite.com", having been given the public IP of the load balancer by DNS. 
- Hostname is a HTTP header, and no HTTP requests have been sent yet, because they cannot be encrypted until the TLS handshake is complete.
- The load balancer receives a connection and it can see the IP headers like source and destination, the destination being its own public IP, but it does not know the hostname because it hasn't been sent yet.
- The LB, having multiple TLS certificates for its different hosts, now **cannot perform the TLS handshake**, because it doesn't know which hostname (and therefore certificate) the client needs.
- So the LB would therefore:
	- Have to require a separate public IP for each of its hosts, in order to know which cert to provide by reading the IP headers.
	- Provide a default certificate. Which **will not** (and cannot possibly since the server doesn't know) match the intended hostname of the client, so the client cannot be sure it's connected to the genuine server for its target and not a bad actor fake server trying to steal details, so it will throw up a warning for the user.
	- The client has a list of valid "signs" or can check with certificate authorities if it can't verify the cert itself, so if the server tried to provide a cert for the right hostname but the wrong "sign" this would also be detected.

It used to be like this because TLS was designed before adoption of virtual hosting, where multiple domains share 1 IP address.

With SNI:
- The client sends the intended hostname as part of the TLS handshake in the Client Hello message.
- The load balancer can select the right certificate to provide to the client for the host name it wants. And the TLS handshake can be completed.