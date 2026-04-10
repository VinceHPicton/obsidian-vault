Anywhere where you have a go.mod file is itself a go module.

To publish your go module, or a new version of it (any new commit pushed can be a new version) do the following:

    git add .
    git commit -m "my new version message"
    git tag v1.2.3
    git push origin v1.2.3

Importers can fetch specific versions like this: `go get gitlab.com/yourname/yourmodule@v1.2.3` And if they don't specify a version, Go resolves the highest available non‑prerelease version.


### Enforcement of breaking changes in Go modules:

In semantic versioning, changing a version from eg: 1.2.3 => 2.0.0 is defined as a _breaking change_

If you do this in Go modules, you must add a /v2 to the module path which is at the top of your go.mod file: `module github.com/yourname/yourmodule/v2`

And you must also of course give it the git tag, of in this case, 2.0.0.

If you don't do this, Go will treat your module version as invalid.