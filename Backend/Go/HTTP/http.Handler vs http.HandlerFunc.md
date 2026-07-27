### `http.Handler` — the interface

```go
type Handler interface {
	ServeHTTP(ResponseWriter, *Request)
}
```

That's it. Anything with a `ServeHTTP(w http.ResponseWriter, r *http.Request)` method satisfies this interface — a struct, a closure wrapped in an adapter, whatever. This is the thing routers, middleware, and `http.ListenAndServe` actually operate on. It's the abstraction.

### `http.HandlerFunc` — one concrete adapter that satisfies it

```go
type HandlerFunc func(ResponseWriter, *Request)

func (f HandlerFunc) ServeHTTP(w ResponseWriter, r *Request) {
	f(w, r)
}
```

`HandlerFunc` is a function type with a `ServeHTTP` method bolted onto it. The method body just calls the function itself. This is a small but clever trick in the standard library: it lets you take an ordinary function and turn it into something that satisfies `Handler`, without writing a whole struct.

So when you write:
```go
func Hello(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "hello world")
}
```

`Hello` on its own is just a function — it does _not_ satisfy `Handler` yet, because it has no `ServeHTTP` method. Wrapping it, `http.HandlerFunc(Hello)`, converts it into something that does.

### Why this distinction matters for middleware

`Handler` is strictly more general than `HandlerFunc`. Every `HandlerFunc` is a `Handler` (via the adapter), but not every `Handler` is a `HandlerFunc` — plenty of real handlers are structs:

```go
type UserHandler struct {
	db *sql.DB
}

func (h *UserHandler) ServeHTTP(w http.ResponseWriter, r *http.Request) {
	// has access to h.db, no closures needed
}
```

`*UserHandler` satisfies `Handler`. It is not a `HandlerFunc`, and there's no way to make it one without writing an adapter closure around it.

So if your `Middleware` type is defined as:

```go
type Middleware func(http.HandlerFunc) http.HandlerFunc
```

it can _only_ ever wrap plain functions. Hand it a `*UserHandler`, a third-party router's handler, or anything struct-based, and it flatly won't compile — you'd have to first wrap it in an adapter (`http.HandlerFunc(h.ServeHTTP)`) just to satisfy the middleware's input type, which is backwards and annoying.

Whereas:
```go
type Middleware func(http.Handler) http.Handler
```

accepts _anything_ — functions (auto-converted) and structs alike — because `http.Handler` is the interface everything already satisfies or can trivially satisfy.

### In practice

You almost never need to think about this conversion explicitly, because Go does it for you at call sites. 

The practical rule of thumb: **write middleware types and constructors in terms of `http.Handler`**, and only reach for `http.HandlerFunc` at the leaves — i.e., when you're wrapping a bare function literal to hand it to something expecting a `Handler`.