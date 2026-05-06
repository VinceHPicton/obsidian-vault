
You should basically always use pxgpool.Pool not pgx.Conn

The pool handles:
- multiple concurrent requests
- reusing connections
- limiting max DB connections
- health/lifetime management

Most general transactions like Exec() Query() etc are designed to be the same with Pool vs Conn, the main difference is in transactions.