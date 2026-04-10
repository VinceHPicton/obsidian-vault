
At a high level, say you want to write a new unitconversions go module

- You'd create a new repo and clone the empty repo
- Now locally: you'd init your go module with `go mod init`
- Write your code
- Use the workflow in [[Publishing a go module]] to `git tag` your commit for versioning.
- You'd then be able to use `go get [module address]` to import the code to whichever services you want.

