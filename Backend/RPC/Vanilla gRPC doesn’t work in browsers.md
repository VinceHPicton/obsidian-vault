- gRPC relies on **HTTP/2 streams with a custom binary protocol**.
- Browser JS can’t create or parse these streams the way a gRPC client expects.
- So a browser cannot talk directly to a gRPC server without a **translation layer**.
    - This is what **grpc-web** does: it turns gRPC into normal HTTP requests/responses (unary calls) and SSE/chunked responses (for streaming).


**JavaScript in the browser doesn’t give you raw access to HTTP/2 streams or frames**.
- `fetch()` and `XMLHttpRequest` abstract away HTTP/2 framing.
- You can send requests and receive responses, but you **cannot handle gRPC’s streaming frames or trailers directly**.