| Scenario                       | Go-to pgxpool method              | Success check                       | Example                      |
| ------------------------------ | --------------------------------- | ----------------------------------- | ---------------------------- |
| Insert 1 row, no return        | `Exec`                            | `RowsAffected() == 1`               | [[Insert one row]]           |
| Insert 1 row, return id/object | `QueryRow`                        | `Scan(...)`, handle error           | [[Insert one row]]           |
| Insert many rows               | `CopyFrom` or `Exec` multi-values | returned count / `RowsAffected()`   | [[Insert bulk rows]]         |
| Update 1 row                   | `Exec`                            | `RowsAffected() == 1`               | [[Update one row]]           |
| Update many rows               | `Exec`                            | `RowsAffected() >= expected/min`    | [[Update many rows]]         |
| Delete 1 row                   | `Exec`                            | `RowsAffected() == 1`               | [[Delete rows]]              |
| Delete many rows               | `Exec`                            | `RowsAffected()` as needed          | [[Delete rows]]              |
| Get 1 row                      | `QueryRow`                        | `Scan(...)`; check `pgx.ErrNoRows`  | [[Get one row]]              |
| Get many rows                  | `Query`                           | iterate `rows.Next()`, `rows.Err()` | [[Get many rows]]            |
| Check existence                | QueryRow + EXISTS                 | .Scan(&exists) (exists bool)        | [[Check existence of a row]] |
Main rule of thumb: **`Exec` for commands, `QueryRow` for exactly one returned row, `Query` for many returned rows, `CopyFrom` for bulk inserts, transaction when multiple statements must succeed/fail together.**