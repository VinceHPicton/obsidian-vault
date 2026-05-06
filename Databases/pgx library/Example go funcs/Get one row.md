```
func (s *Store) GetUser(ctx context.Context, id int64) (User, error) {
    const q = `
        SELECT id, email, name
        FROM users
        WHERE id = $1
    `

    var u User
    err := s.pool.QueryRow(ctx, q, id).Scan(&u.ID, &u.Email, &u.Name)
    if errors.Is(err, pgx.ErrNoRows) {
        return User{}, ErrNotFound
    }
    if err != nil {
        return User{}, err
    }

    return u, nil
}
```

