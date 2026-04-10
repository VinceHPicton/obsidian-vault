A Go variable which tells the Go toolchain which modules are private, so it should treat them differently from public modules.

By default running [[go mod download]] tries to fetch modules through proxy.golang.org, but if the module is private it won't be on there, so you use GOPRIVATE to tell Go to fetch directly from the origin given. 

Set 1 or more different wildcarded URLs: 
```
go env -w GOPRIVATE=*.cl.local,*.github.mycompany.com
```