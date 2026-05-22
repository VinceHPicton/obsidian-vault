Essentially the same as [[Timeouts]] but you give them an exact time rather than a duration.


```
WithTimeout(ctx, duration)
```

is equivalent to:

```
WithDeadline(ctx, time.Now().Add(duration))
```

So internally here is no real behavioural difference