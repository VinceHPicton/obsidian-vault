Go modules use semantic versioning (info at [https://semver.org/](https://semver.org/)), and handles versioning by looking at a go.mod and a go.sum file which are checked-out to git. You can think of these files are very much equivalent to NPM's dependency tracking files: package.json/package-lock.json.

go.mod == package.json and go.sum == package-lock.json