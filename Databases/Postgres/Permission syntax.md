Example snippet from running \list (list DBs) in psql:

```
Access privileges
-----------------------------

=c/admin     +
admin=CTc/admin
```

This is Postgres’ slightly cursed permission syntax.

Roughly:

- `=` → applies to PUBLIC (everyone)
- `c` → CONNECT
- `T` → TEMP tables
- `C` → CREATE

So:

```
=c/admin
```

→ everyone can connect

```
admin=CTc/admin
```

→ admin can:

- Create tables
- Use temp tables
- Connect