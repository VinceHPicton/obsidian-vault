Channels are a core concurrency [[Primitive]] used to send data between goroutines safely. You can think of them as portals or pipes, between goroutines.

One of the core Go idioms is: **don't share memory to communicate, communicate to share memory** - this means don't give 2 goroutines access to the same variable (mutable state), send copies of that data between them (send messages between them). 

**Channels let you do this.**

### Sending and receiving

```
ch <- 42   // send value into channel
x := <-ch  // receive value from channel
```

## Unbuffered vs buffered channels

### Unbuffered (synchronous)

```
ch := make(chan int)

go func() {
    ch <- 1 // blocks until someone receives
}()

val := <-ch // blocks until someone sends
```

**Key property:** send and receive rendezvous.

This is useful for:

- synchronisation
- handoff patterns

---

### Buffered (asynchronous, up to capacity)

```
ch := make(chan int, 3)

ch <- 1
ch <- 2
ch <- 3 // ok
ch <- 4 // blocks (buffer full)
```

**Key property:** sender only blocks when buffer is full.

Useful for:

- throttling work
- decoupling producer/consumer speeds

---

## Directional channels

You can restrict usage in function signatures:

```
func producer(ch chan<- int) {
    ch <- 10
}

func consumer(ch <-chan int) {
    fmt.Println(<-ch)
}
```

- `chan<- int` = send-only
- `<-chan int` = receive-only

The underlying channel is still bidirectional, but you can write a function that just receives a **restricted view of a pre-existing channel**, in order to improve correctness and readability.

## Closing channels

A channel can be closed:

```
close(ch)
```

### Rules:

- Only the goroutine which owns the channel should close it
- Never send on a closed channel (panic)

### Receiving from a closed channel:

```
v, ok := <-ch
```

- `ok == false` means channel is closed **and** drained

### Common pattern: range over channel

```
for v := range ch {
    fmt.Println(v)
}
```

Loop exits automatically when channel is closed.

---

# Important points:

### If consumers use `range`, you must close:

```
for v := range ch { ... } // will deadlock if channel (ch) never closed
```

### Do not send on closed channel
```
close(ch)
ch <- 1 // panic
```

