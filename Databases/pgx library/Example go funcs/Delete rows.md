```
func (s *Store) DeleteUser(ctx context.Context, id int64) error {
    tag, err := s.pool.Exec(ctx, `
        DELETE FROM users
        WHERE id = $1
    `, id)
    if err != nil {
        return err
    }
    if tag.RowsAffected() == 0 {
        return ErrNotFound
    }
    if tag.RowsAffected() != 1 {
        return fmt.Errorf("expected 1 row deleted, got %d", tag.RowsAffected())
    }
    return nil
}
```