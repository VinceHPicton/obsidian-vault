A `go.work` file is used to define a **Go workspace**, which lets you work on multiple modules together locally as if they were one project.

### The core problem it solves

Normally, Go modules are isolated. If you have:

- `service-a`
    
- `service-b`
    
- `shared-lib`
    

…and `service-a` depends on `shared-lib`, Go will by default fetch `shared-lib` from its module path (e.g. GitHub), not your local copy. That’s annoying when you’re developing both at the same time.

### What `go.work` does

A `go.work` file tells Go:

> “Use these local modules instead of fetching them remotely.”

### Example

```bash
go work init ./service-a ./service-b ./shared-lib
```

This creates a `go.work` file like:

```go
go 1.22

use (
    ./service-a
    ./service-b
    ./shared-lib
)
```

Now:

- If `service-a` imports `shared-lib`, it uses your **local version**
    
- No need for `replace` directives in `go.mod`
    
- Changes in `shared-lib` are immediately visible to both services
    

### Why it exists (vs older approach)

Before `go.work`, you’d use this in `go.mod`:

```go
replace github.com/you/shared-lib => ../shared-lib
```

That works, but:

- It pollutes `go.mod` (bad for committing)
    
- It’s per-module, not centralised
    
- Easy to forget/remove
    

`go.work` fixes that by:

- Keeping local dev config **separate**
    
- Working across multiple modules at once
    
- Being easy to ignore in version control if needed
    

### When you should use it

Use `go.work` if you:

- Are developing multiple Go modules together
    
- Have a monorepo with separate modules
    
- Want to avoid `replace` hacks
    

Don’t bother if:

- You only have a single module
    
- You’re just consuming published dependencies
    

### Subtle but important detail

`go.work` only affects **your local build environment**. It does _not_ change how your module behaves for others or in CI unless the `go.work` file is also present there.

---

If you’ve ever used something like a monorepo tool (e.g. npm workspaces), this is basically Go’s minimal, no-nonsense version of that.