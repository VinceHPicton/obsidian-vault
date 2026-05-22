# Example timeline

```
ctx, cancel := context.WithTimeout(
	context.Background(),
	3*time.Second,
)
defer cancel()

select {
case <-ctx.Done():
	fmt.Println(ctx.Err())
}
```

Execution:

```
t=0s  -> select starts blocking
t=1s  -> still blocked
t=2s  -> still blocked
t=3s  -> timeout occurs
t=3s  -> ctx.Done() channel closes
t=3s  -> select wakes up
t=3s  -> prints "context deadline exceeded"
```

Example: https://goplay.tools/snippet/V6Gzyf62eii

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

is completely different.

Because `default` makes `select` non-blocking.

It becomes:

> “check immediately and continue if nothing is ready”

### Without `default`, `select` blocks.

### With `default`, it polls.

