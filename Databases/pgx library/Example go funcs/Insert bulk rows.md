```
func (s *Store) BulkCreateUsers(ctx context.Context, users []User) (int64, error) {
    rows := make([][]any, 0, len(users))
    for _, u := range users {
        rows = append(rows, []any{u.Email, u.Name})
    }

    n, err := s.pool.CopyFrom(
        ctx,
        pgx.Identifier{"users"},
        []string{"email", "name"},
        pgx.CopyFromRows(rows),
    )
    if err != nil {
        return 0, err
    }

    if n != int64(len(users)) {
        return n, fmt.Errorf("expected %d rows inserted, got %d", len(users), n)
    }

    return n, nil
}
```