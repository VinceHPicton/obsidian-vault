# Why would anyone create multiple DBs in 1 postgres instance?

If you want **strongly isolated separate environments** within the same [[Instance or cluster|cluster]], such as for prod/dev/staging 


# Why cant I see all my DBs in DBeaver?
Possible because you didn't tick "show all DBs"


# So why does each DB in DBeaver list roles, when roles are meant to be at the instance level?
Because although roles are **defined at the instance (cluster) level**, their _relevance is per database_, tools like DBeaver present them within each database context to show how those global roles interact with that specific database
i.e. which roles have privileges there, own objects there, or can connect—so you’re not seeing “database-specific roles,” you’re seeing **instance-wide roles filtered through the lens of that database’s permissions and objects**, which is far more useful in practice than a single flat list.