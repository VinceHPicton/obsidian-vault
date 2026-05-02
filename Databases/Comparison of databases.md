### PostgreSQL
- **Strength:** Feature-rich and highly extensible (handles complex queries + many use cases)
- **Weakness:** Operational overhead (vacuuming, tuning, bloat)

### MySQL
- **Strength:** Simple and good for read-heavy workloads
- **Weakness:** Less powerful/expressive than Postgres

### SQLite - DB is just a file
- **Strength:** Zero-config, extremely lightweight (just a file)
- **Weakness:** Poor concurrency, not for distributed systems
- **Use case**: Mobile apps, local caching

### Microsoft SQL Server
- **Strength:** Excellent tooling and enterprise integration with Microsoft
- **Weakness:** Expensive and ecosystem-locked

### Oracle Database
- **Strength:** Extremely powerful and scalable for mission-critical systems
- **Weakness:** Expensive and vendor lock-in

### MariaDB - alternative MySQL (a fork of MySQL)
- **Strength:** MySQL-compatible with some performance improvements
- **Weakness:** Smaller ecosystem and momentum