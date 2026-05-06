### Use SELECT EXISTS
```
func (s *Store) UserExists(ctx context.Context, email string) (bool, error) {
    const q = `
        SELECT EXISTS (
            SELECT 1
            FROM users
            WHERE email = $1
        )
    `

    var exists bool
    err := s.pool.QueryRow(ctx, q, email).Scan(&exists)
    if err != nil {
        return false, err
    }

    return exists, nil
}
```

### NOT SELECT LIMIT 1:
This is worse because it's abusing errors for control flow and needs a dummy variable, it's just a bit awkward in Go
```
func (s *Store) UserExists(ctx context.Context, email string) (bool, error) {
    const q = `
        SELECT 1
        FROM users
        WHERE email = $1
        LIMIT 1
    `

    var dummy int
    err := s.pool.QueryRow(ctx, q, email).Scan(&dummy)

    if err == nil {
        return true, nil
    }
    if errors.Is(err, pgx.ErrNoRows) {
        return false, nil
    }
    return false, err
}
```