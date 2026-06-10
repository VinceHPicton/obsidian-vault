A Go workspace (`go.work`) lets you work on **multiple Go modules together as if they were one project**, without having to publish modules or use `replace` directives in `go.mod`.

For example, imagine you have:
```
~/projects/
├── api/
│   └── go.mod
├── shared/
│   └── go.mod
└── go.work
```

Without a workspace, if `api` depends on `shared`, you'd typically need:
```
replace github.com/you/shared => ../shared
```
inside `api/go.mod`.

With a workspace, your `go.work` contains:
```
go 1.26

use (
    ./api
    ./shared
)
```

Now when you run commands from the workspace root:

```
go test ./...
go build ./...
```

Go automatically uses the local `shared` module instead of looking for a published version.