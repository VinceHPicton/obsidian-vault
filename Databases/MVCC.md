Multiversion concurrency control is a technique to allow daatabases to concurrently handle reads and writes without blocking eachother. It achieves this by keeping multiple versions of rows.

# How it works

Imagine a row:
`id: 1, balance: 100`

### Transaction A (read)
- Sees: `balance = 100`
### Transaction B (write)

- Updates balance → 200
- **Creates a new row version**, doesn’t overwrite the old one

Now internally you have:

Version 1: balance = 100 (visible to old transactions)  
Version 2: balance = 200 (visible to new transactions)

Transaction A still sees **100**, even though the update happened.


“treat the database like an append-only timeline, and let each transaction read its own version of reality.”