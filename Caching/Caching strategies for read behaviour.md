## Cache-aside (lazy loading) — most common
Checks cache for value when requested, if found return result, if not query backend, return and save result
Risks the [[Cache stampede (thundering herd)|thundering herd]] problem


