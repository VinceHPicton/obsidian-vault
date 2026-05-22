

Context timeouts lets you auto cancel after a specific duration, but you must check `ctx.Done()` or more rarely `ctx.Err()` to do so.

## Create a timeout context

```
ctx, cancel := context.WithTimeout(
    context.Background(),
	5*time.Second,
)
defer cancel()
```

Creates a child context that automatically cancels after 5 seconds.

---

# Always call `cancel()`

```
defer cancel()
```

Even if the timeout will happen automatically.

Reason:
- releases timers/resources early
- prevents leaks
- idiomatic Go
- If doing this causes a worker to be terminated early, the deferred cancel is revealing the design mistake rather than causing it.

Example of how defer cancel() could prematurely end work:
```
func startWorker() {
	ctx, cancel := context.WithCancel(context.Background())
	defer cancel()

	go worker(ctx)
}
```
-> worker is cancelled immediately as startWorker() exits.

### Correct version:
```
func startWorker(ctx context.Context) {
	go worker(ctx)
}
```
### The deeper rule

Contexts should not outlive their owner.

If goroutines need to continue after a function exits:
- the context should usually be owned higher up
- or cancellation should be controlled elsewhere


---

# Timeout does NOT magically stop code

Context cancellation is cooperative.

Your code (or library) must observe the context...

---

# Idiomatic cancellation check

## Preferred

```
select {
case <-ctx.Done():
	return ctx.Err()
}
```

## Simpler polling style

```
if ctx.Err() != nil {    return ctx.Err()}
```

Less common for concurrent code.

---
# Most common real-world usage

Pass context into APIs:

```
db.QueryContext(ctx, query)http.NewRequestWithContext(ctx, ...)exec.CommandContext(ctx, ...)
```

These APIs handle cancellation internally.

---

# Common loop pattern

```
for {
    select {
    case msg := <-messages:
        handle(msg)

    case <-ctx.Done():
        return ctx.Err()
    }
}
```

---

# Common timeout work pattern

```
select {
case result := <-resultChan:
    return result

case <-ctx.Done():
    return ctx.Err()
}
```


---

# Common `ctx.Err()` values

## Timeout exceeded

```
context deadline exceeded
```

## Manually cancelled

```
context canceled
```
