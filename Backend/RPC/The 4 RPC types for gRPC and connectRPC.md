**Unary RPC**
Client sends **one** request, server sends **one** response.

**Server streaming RPC**
Client sends one request, server sends a stream of responses.
- Eg: Client requests stock price data, server sends stream of live updates.

**Client streaming RPC**
Client sends a stream of requests, server responds once.

**Bidirectional streaming RPC**
Both client and server are  streaming messages to eachother.

