## 1. The core idea: GRANT / REVOKE

Everything revolves around:

```
GRANT <privileges> ON <object> TO <role>;REVOKE <privileges> ON <object> FROM <role>;
```

Example:

```
GRANT SELECT, INSERT ON TABLE users TO developers;
```


## 2. Privileges depend on the object type

Different objects support different permissions:

### Tables

- `SELECT` → read
- `INSERT` → add rows
- `UPDATE` → modify rows
- `DELETE` → remove rows

```
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLE users TO developers;
```

---

### Schemas

- `USAGE` → can access objects inside
- `CREATE` → can create tables in it

```
GRANT USAGE, CREATE ON SCHEMA public TO developers;
```

👉 Common mistake: forgetting `USAGE` and wondering why access fails

---

### Databases

- `CONNECT` → can connect
- `CREATE` → can create schemas
- `TEMP` → temp tables

```
GRANT CONNECT ON DATABASE myapp TO developers;
```

## 3. Roles inherit permissions

You rarely grant directly to users:

```
GRANT developers TO alice;
```

Then:

```
GRANT SELECT ON users TO developers;
```

👉 `alice` automatically gets it

This is the **standard pattern**:

> roles = permission bundles, users = identities


## 4. “ALL TABLES” vs future tables (important)

This catches a lot of people:

```
GRANT SELECT ON ALL TABLES IN SCHEMA public TO developers;
```

❌ Only applies to existing tables

To handle future ones:

```
ALTER DEFAULT PRIVILEGES IN SCHEMA publicGRANT SELECT ON TABLES TO developers;
```

👉 You almost always want both

## 5. Ownership overrides everything

If a role **owns** an object:

- It automatically has full control
- It doesn’t need explicit GRANTs

This is why production setups often:

- use a separate **owner role**
- and separate **app roles**

---

## 6. The `public` trap

By default, Postgres gives broad access via `PUBLIC` (everyone):

```
=c/postgres
```

This can mean:

- anyone can connect
- sometimes more than you expect

In stricter setups you’ll often:

```
REVOKE ALL ON DATABASE myapp FROM PUBLIC;
```

## 7. Reading the weird privilege syntax (`\l`, `\dp`)

Example:

```
= c / adminadmin = CTc / admin
```

Roughly:

- `=` → PUBLIC (everyone)
- `c` → CONNECT
- `T` → TEMP
- `C` → CREATE

You don’t need to memorise this—just know it exists.

---

## 8. Practical “good enough” setup for apps

A very typical pattern:
```
-- Owner (no login)
CREATE ROLE app_owner;

-- App user
CREATE ROLE app_user WITH LOGIN PASSWORD '...';

-- DB owned by owner
CREATE DATABASE myapp OWNER app_owner;

\c myapp

-- Schema owned by owner
CREATE SCHEMA app AUTHORIZATION app_owner;

-- Allow app to use it
GRANT USAGE ON SCHEMA app TO app_user;

-- Table access
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA app TO app_user;

-- Future tables
ALTER DEFAULT PRIVILEGES IN SCHEMA app
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO app_user;

```


**Ownership = control**  
**GRANT = access**  
**Roles = reusable permission sets**


