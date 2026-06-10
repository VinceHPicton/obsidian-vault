Depends on what you want to accomplish.

It's a way to organize data much like folders on a harddrive. A database server can contain multiple databases. Each database can contain multiple schemas. Each schema can contain multiple relations. A database connection can only be connected to one database and can only access data from that database. It can however access data from all schemas in that database and even join relations across schemas.

I would say most won't need multiple schemas. So unless you see a reason to create multiple schemas go with public.

I can imagine the following reasons to consider using more schemas (but most can also be accomplished by a single schema)

- avoid tables names to clash between projects (e.g. 2 projects both have a table called user)
- To define clear responsibilities on data ownership or relationship between data. (e.g. Schema A contains all customer data and schema b contains all analytic data)
- Some extension should only be used with specific tables (e.g. Don't want postgis extension for main schema)
- Easier ACL control (access can be defined on schema level)
- Easier table space definitions (table space can be defined for whole schemas)
- Datamining / analysis where you import different foreign databases into one database with different schemas.