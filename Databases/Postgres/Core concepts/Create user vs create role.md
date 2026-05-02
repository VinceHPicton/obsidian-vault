
These 2 commands are the same:
```
CREATE USER alice WITH PASSWORD 'secure_password';
CREATE ROLE alice WITH LOGIN PASSWORD 'secure_password';
```

CREATE USER is just a convenience shortcut


# Q: if you tried to omit the WITH PASSWORD what would happen?

The command would still succeed—`alice` would be created as a login role, but **with no password set**, so password-based authentication would fail; whether you can actually log in depends on your `pg_hba.conf` settings (e.g. `trust` might allow access without a password, whereas `md5`/`scram-sha-256` would block it).