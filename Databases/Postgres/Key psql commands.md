## Core navigation

- `\l` → list databases
- `\c mydb` → connect to a database
- `\conninfo` → show current connection details

---

## Listing objects

- `\dt` → list tables in current schema
- `\dt *.*` → list tables across all schemas
- `\dn` → list schemas
- `\dv` → list views
- `\df` → list functions
- `\du` → list roles (users)

- `\dp` → show table permissions

---

## Inspecting structure (very useful)

- `\d table_name` → describe a table (columns, types, indexes)
- `\d+ table_name` → more detail (size, storage, etc.)
- `\d schema_name.*` → list everything in a schema

---

## Permissions & ownership

- `\dp` → show table permissions
- `\l` → also shows database-level permissions

---

## Query execution helpers

- `\x` → toggle expanded output (much nicer for wide tables)
- `\timing` → show query execution time
- `\watch 1` → rerun a query every second

---

## File & scripting

- `\i file.sql` → run a SQL file
- `\o output.txt` → send output to file
- `\copy` → copy data to/from CSV (client-side)

---

## Help & discovery (underrated)

- `\?` → list all psql commands
- `\h SELECT` → SQL help for a command

---

## Exit

- `\q` → quit