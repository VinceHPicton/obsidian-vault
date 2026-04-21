When you randomly get a large number of cache misses all at once, spiking load on the DB.

Probability says this will occur sometimes given certain caching strategies, like lazy loading.

Ways to mitigate:
- **Coalesce requests**, eg many parts of the stampede could be the same request that all missed.
- Stale-while-revalidate: serve the stale data for older results which you refresh the data.