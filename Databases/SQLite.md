SQLite is not a server like Postgres or other DBs are, it's a library that edits a single file on disk.

Only 1 writer is allowed at a time, no write concurrency!

Your app talks directly to the software, there are no network calls to a server.

It's used for local caching or small devices like mobiles.