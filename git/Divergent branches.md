If 2 branches have diverged, it means they **both** have commits the other does not

This commonly happens between your local and the remote - if you have unpushed commits and the remote also has new commits.

There are 3 main strategies for pulling, only the first 2 resolve this situation:

1. Merge (default behaviour - )
This is the safe but creates a merge commit.
Permanently configure: `git config pull.rebase false`
Or set this just once: `git pull --no-rebase`

2. Rebase (preserves commit history, changes SHAs)
This will **replay your local commits** on top of the remote branch, creating a linear history. This does however change the hashes of your commits, because part of the SHA is a timestamp and other metadata which will change when they're reapplied or something.
Permanently configure: `git config pull.rebase true`
Or set this just once: `git pull --rebase`

3. Fast-forward only
This will only pull if Git can **fast-forward** your branch (i.e. no local commits). If not, it will error out.
Permanently configure: `git config pull.ff only`
Or set this just once: `git pull --ff-only`

