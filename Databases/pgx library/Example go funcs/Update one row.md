```
func (s *Store) UpdateUserName(ctx context.Context, id int64, name string) error {
    tag, err := s.pool.Exec(ctx, `
        UPDATE users
        SET name = $1
        WHERE id = $2
    `, name, id)
    if err != nil {
        return err
    }
    if tag.RowsAffected() == 0 {
        return ErrNotFound
    }
    if tag.RowsAffected() != 1 {
        return fmt.Errorf("expected 1 row updated, got %d", tag.RowsAffected())
    }
    return nil
}
```

