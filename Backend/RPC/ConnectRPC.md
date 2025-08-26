ConnectRPC (from Buf) is like a **modern, browser-friendly version of gRPC**:

- Works over **plain HTTP/1.1 and HTTP/2** (gRPC uses HTTP/2 streams only).
- Designed to work great in **browsers, mobile apps, and servers**. [[Vanilla gRPC doesn’t work in browsers]], making it awkward to use in browsers.
- Focuses on **interoperability** → a ConnectRPC service can also be used as:
    - **gRPC** (native gRPC clients work),
    - **gRPC-Web** (browser clients work),
    - **Connect** (ConnectRPC clients work).
This is the big win: **one service definition, multiple protocols for free.**

### Why use ConnectRPC over REST?
ConnectRPC uses strong contracts, you define your schema in a proto file, and that single source of truth is used to generate code on both the client and server.
- In Go → you get a `User` struct with `id int64, name string`.
- In TypeScript → you get a `User` interface with `id: number, name: string`.

If you change the API (the proto file), clients and servers will **fail at compile time** (or at least during codegen), instead of only breaking in production.
REST APIs usually rely on _conventions and docs_ (weak contracts - they can be broken causing errors), while gRPC/ConnectRPC use _formal schemas with code generation_ (strong contracts - they can't be broken as the code is generated).

### How ConnectRPC uses HTTP
- ConnectRPC is **HTTP-native**:
    - It uses plain **HTTP requests/responses** that look normal to any proxy, CDN, or browser.
    - Unary RPCs = just a POST with JSON or Protobuf body.
    - Streaming RPCs = implemented via **chunked responses** or **Server-Sent Events (SSE)**, which browsers can handle directly.
- Works over **HTTP/1.1 or HTTP/2** interchangeably.
- Because it sticks closer to normal HTTP, browsers, middleboxes, and tools (like cURL, Postman) can interact with it more easily.

TS connectRPC client call:
```
const user = await client.userService.getUser({ id: 123 });
console.log(user.name); // "Alice"
```
