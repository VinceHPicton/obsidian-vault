|Config Key|Values|Description|
|---|---|---|
|`pull.rebase`|`false` / `true` / `merges` / `interactive`|Choose how `git pull` reconciles divergent history|
|`pull.ff`|`true` / `false` / `only`|Controls fast-forward behavior|
|`rebase.autoStash`|`true` / `false`|Stash uncommitted changes before rebase|
|`rebase.backend`|`apply` / `merge`|Choose the rebase engine (rarely needed)|
You can fine-tune rebase behavior with:
- `pull.rebase = merges`  
    → Preserves local merge commits during rebase  
    (good for topic branches)
- `pull.rebase = interactive`  
    → Runs an **interactive rebase** when pulling  
    (lets you edit commits before they're applied)
    
But these only make sense when `pull.rebase = true`.

The fast-forward settings:

|`ff = true` | Use fast-forward **if possible**, otherwise do a **merge commit**|
|`ff = only` | Use fast-forward **only** — otherwise, **fail with an error**|