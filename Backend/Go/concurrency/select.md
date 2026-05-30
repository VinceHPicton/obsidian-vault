`select` in Go is _almost exclusively a concurrency construct_. It exists to let a goroutine wait on multiple communication operations at once, primarily **channels**.

# `select` (single statement)

A **one-off decision point**: it waits on multiple channel operations and proceeds with whichever becomes ready first.

```
select {
case v := <-ch1:
    fmt.Println("ch1:", v)
case v := <-ch2:
    fmt.Println("ch2:", v)
}
```
### What it does

- Blocks until _one_ case can proceed
- Picks a ready case (randomly if multiple ready)
- Executes it once
- Then it’s done

## Typical uses of `select` single statement

### 1. Timeouts

```
select {
case v := <-ch:
    fmt.Println(v)
case <-time.After(2 * time.Second):
    fmt.Println("timeout")
}
```

### 2. Non-blocking send/receive

```
select {
case ch <- 1:
    fmt.Println("sent")
default:
    fmt.Println("channel not ready")
}
```

---

# `for { select { ... } }` (looped select)

This is a **continuous event-processing loop**.

```
for {
    select {
    case v := <-ch:
        fmt.Println("received:", v)
    case <-stop:
        fmt.Println("stopping")
        return
    }
}
```

### What it does

- Repeats forever (or until you `return`/break)
- Keeps reacting to channel events
- Turns Go into an **event loop**

---

# Why `select` is useful

Because you can wait on MULTIPLE things simultaneously.

Example:

```
select {
case msg := <-messages:
	handle(msg)

case <-ctx.Done():
	return ctx.Err()
}
```

This means:

> “whichever happens first:
> 
> - a message arrives
> - cancellation occurs”

That’s one of the most important concurrency patterns in Go.

---

# Important subtlety

This:

```
select {
case <-ctx.Done():
	return
default:
	fmt.Println("not cancelled")
}
```

is completely different to the above.

**Because `default` makes `select` non-blocking.**

It becomes:

> “check immediately and continue if nothing is ready”

### Without `default`, `select` blocks.

### With `default`, it polls (and falls back if nothing ready).


# Using select for an inline timeout
```
ch := make(chan int)

go func() {
	// Try either of these
	// time.Sleep(time.Second * 1)
	time.Sleep(time.Second * 3)
	ch <- 1
}()

select {
case res := <-ch:
	fmt.Println(res)

case <-time.After(2 * time.Second):
	fmt.Println("timeout")
}
```
Example of this: https://goplay.tools/snippet/-_P4qj4ja1B
