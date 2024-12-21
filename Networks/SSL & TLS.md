Secure sockets layer is a [[Protocol]] which is the predecessor to modern TLS encryption (transport layer security).

TLS is also another protocol, the more modern version which is actually used now.

Websites that implement SSL/TLS have HTTPS in it's url, HTTPS refers to the combination of HTTP at layer 7 and TLS at layer 6.

Often people refer to what is really TLS as SSL, SSL is now deprecated and not used. So an SSL certificate is **really a TLS certificate**.

**What is a SSL certificate?**
It's like an ID badge that proves someone is who they say they are, it also **includes a public encryption key** for the clients to use.

Great video: https://www.youtube.com/watch?v=j9QmMEWmcfo

HTTPS/TLS use [[asymmetric encryption]] to securely exchange keys and establish a 2-way secure channel for [[symmetric encryption]]. This is done because assymetric encryption is computationally costly and so unsuitable for bulk data transfer for performance reasons. 

**How HTTPS works**
- TCP handshake occurs to establish TCP connection between browser and server.
- Certificate check
	- 1. Client Hello (includes things like TLS version & cipher suite which client can support)
	- 2. Server Hello (Server chooses the version and cipher suite it wants to use)
	- 3. Certificate - server sends SSL certificate, **which includes the public key of server** among other things
	- 4. Server Hello Done
- Key exchange
	- 1. Client generates and encrypts its session key **using the servers public key**
	- 2. Now both sides hold the **session key** and can communicate with symmetric encryption, which is **computationally much cheaper than assymetric**.
- Data transmission now takes place using the session key via symmetric encryption