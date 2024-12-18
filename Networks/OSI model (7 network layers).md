
The OSI model is one way to understand how networks function, the model makes more sense by thinking of the layers as 4, combining layers 5-7 into 1.

See the image for where different protocols sit
![[OSI model IMG.png]]

- The real data is sent over the cables as bits, so these layers are abstractions over this to allow us to make sense of the data.
- Layer 6 is where encryption such as with [[SSL & TLS|SSL]] happens
- Layer 5 is where RPC (remote procedure call) protocol sits

**What it means to go down the layers**
- Each protocol adds metadata called "headers" to the payload (the actual data we want to transmit).
- So at HTTP the headers are things like GET, status codes, "Content-type": "Application/json"
- At the TLS (layer 6), the **payload and all HTTP headers** become **encrypted**, only the TLS handshake info remains unencrypted.
- Lower down, TCP add its headers, things like the destination port
- [[IP]] adds addressing headers like the protocol used above it, IP address.
- This continues to the physical layer, where all the data is finally transmitted as bits.