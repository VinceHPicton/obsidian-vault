```
func (s *Store) ListUsers(ctx context.Context) ([]User, error) {
    const q = `
        SELECT id, email, name
        FROM users
        ORDER BY id
    `

    rows, err := s.pool.Query(ctx, q)
    if err != nil {
        return nil, err
    }
    defer rows.Close()

    var users []User
    for rows.Next() {
        var u User
        if err := rows.Scan(&u.ID, &u.Email, &u.Name); err != nil {
            return nil, err
        }
        users = append(users, u)
    }

    if err := rows.Err(); err != nil {
        return nil, err
    }

    return users, nil
}
```

