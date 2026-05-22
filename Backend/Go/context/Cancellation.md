You can cancel work from the parent:

```
ctx, cancel := context.WithCancel(context.Background())
defer cancel()
```

Any goroutine using that context can detect cancellation:

```
select {
case <-ctx.Done():
    return ctx.Err()
}
```

`ctx.Done()` is a channel that closes when cancelled.