The fundamental identity used for auth in Postgres - it can represent a person, an application, or a group. All databases are owned by a SINGLE role at any given time.

A role can be a [[User]] if it has the login attribute

## Roles ≠ just “users”

Roles can be:

- login roles (actual users)
- group roles (for permissions)

Example:

```
CREATE ROLE developers;
GRANT developers TO alice;
```


