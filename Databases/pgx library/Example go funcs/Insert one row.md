### Collect the returned data
```
func (s *Store) CreateUser(ctx context.Context, email, name string) (int64, error) {
    const q = `
        INSERT INTO users (email, name)
        VALUES ($1, $2)
        RETURNING id
    `

    var id int64
    if err := s.pool.QueryRow(ctx, q, email, name).Scan(&id); err != nil {
        return 0, err
    }

    return id, nil
}
```

### If nothing is returned
```
func (s *Store) CreateUserNoReturn(ctx context.Context, email, name string) error {
    tag, err := s.pool.Exec(ctx, `
        INSERT INTO users (email, name)
        VALUES ($1, $2)
    `, email, name)
    if err != nil {
        return err
    }
    if tag.RowsAffected() != 1 {
        return fmt.Errorf("expected 1 row inserted, got %d", tag.RowsAffected())
    }
    return nil
}
```