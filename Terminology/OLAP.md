Online analytical processing is an approach to database systems where data complex **reading** is prioritized over performance in data writes. This means you are able to make complex queries against the data efficiently for analysis, but availability of the DB is not concern

Data being written to the database is done in **batches** and may take hours or even days to be inputted.

These systems are a primary use case of SQL (RDBMS) databases.

OLAP is the contrasting approach to [[OLTP]] 

OLAP is very often used on **columnar data** - this is where each "row" is actually a column and vice versa:

ROW-based data:
```
1, Alice, Laptop, 1000, 2024-02-06
2, Bob, Phone, 500, 2024-02-06
3, Alice, Tablet, 300, 2024-02-05
```

The same data, COLUMN-based:
```
ID: 1, 2, 3
Customer: Alice, Bob, Alice
Product: Laptop, Phone, Tablet
Amount: 1000, 500, 300
Date: 2024-02-06, 2024-02-06, 2024-02-05
```

It would be easy to find eg SUM(amount) or AVG(amount) with columnar data, but hard to do things like insert a new record, vs row-based,