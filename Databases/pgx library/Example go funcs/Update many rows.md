```
func (s *Store) DeactivateUsers(ctx context.Context, ids []int64) (int64, error) {
    tag, err := s.pool.Exec(ctx, `
        UPDATE users
        SET active = false
        WHERE id = ANY($1)
    `, ids)
    if err != nil {
        return 0, err
    }

    return tag.RowsAffected(), nil
}
```
