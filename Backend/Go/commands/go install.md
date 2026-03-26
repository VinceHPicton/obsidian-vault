
When you run go install package@version Go downloads a go module, builds it with go build, and saves the binary to your [[GOBIN]] (or if that's empty, your [[GOPATH]]/bin)

- It's basically how you install Go tools locally
- It ONLY works for Go programs (they do not have to have a go.mod - making them a module - but they probably will because most go projects have go.mod)
- It does NOT modify your go.mod or your project in ANY WAY
- If you omit a version (ie the @latest or @1.2.1) Go tries to treat the package given as a package in **your current, local, module** - this is a highly confusing and important note. Go does this to avoid ambiguity, as it would otherwise have to assume you meant @latest or something when doing the download of the module.


**1 Caveat:**
If you just run `go install` with no following package, in a go module, Go builds your current project and saves that to [[GOBIN]] (or if that's empty, your [[GOPATH]]/bin)