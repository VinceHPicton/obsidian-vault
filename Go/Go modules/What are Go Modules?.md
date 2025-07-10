
It's Go's way of managing dependencies - just like npm is for node projects.

|Concept|Go Modules|npm Equivalent|
|---|---|---|
|Project definition|`go.mod`|`package.json`|
|Dependency versions|Declared in `go.mod`, resolved in `go.sum`|Declared in `package.json`, resolved in `package-lock.json`|
|Install dependencies|`go mod tidy` / automatic|`npm install`|
|Publish a library|Push to Git (e.g., GitHub)|`npm publish`|
|Import another module|Use import path like `github.com/user/repo`|`require("library")` or `import`|
|Semantic versioning|Fully supported|Fully supported|