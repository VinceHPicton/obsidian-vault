There is always a default schema: `public` in every database

If you don’t specify a schema:

```
SELECT * FROM users;
```

Postgres actually does:

```
SELECT * FROM public.users;
```

