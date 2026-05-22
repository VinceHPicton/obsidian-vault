
# 2. Timeouts

Context timeouts lets you auto cancel after a specific duration, but you must check `ctx.Done()` or more rarely `ctx.Err()` to do so.

