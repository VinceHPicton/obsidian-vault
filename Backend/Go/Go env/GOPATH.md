GOPATH still exists but it's sort of a hangover from the past, it's used to determine where to save binaries and mods if [[GOMODCACHE]] and/or [[GOBIN]] are unset

```
GOPATH='/home/incenticton/go'
```

If [[GOMODCACHE]] is empty Go defaults to $GOPATH/pkg/mod
If [[GOBIN]] is empty Go defaults to $GOPATH/bin