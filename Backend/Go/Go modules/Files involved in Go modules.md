
go.mod === package.json
- Created with **go mod init** my/module
- Example:
```
module github.com/user/myproject

go 1.20

require (
  github.com/sirupsen/logrus v1.9.0
  golang.org/x/net v0.17.0
)
```


go.sum === package-lock.json
- Automatically maintained - not meant for manual editing
- Records the hashes of downloaded modules to verify integrity.
- Ensures builds are reproducable