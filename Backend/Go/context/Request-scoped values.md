Used to pass some data through many layers of code, but I don’t want to thread it through every function parameter.
### They are often discouraged for general use.



# # With context values

```
ctx = context.WithValue(ctx, "requestID", "abc123")
```

Then anywhere down the chain:

```
id := ctx.Value("requestID")
// id = "abc123"
```

No function signature changes needed.


# The _real intended use cases_

The Go authors intended this for **cross-cutting request metadata**, mainly:

## 1. Tracing / observability

- OpenTelemetry span IDs
- request IDs for logs

## 2. Authentication context

- user ID
- roles / permissions (sometimes)

## 3. Debugging / logging correlation

- attach request identity to logs automatically