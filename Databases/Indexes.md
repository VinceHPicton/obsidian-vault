An index is an additional data structure - usually a Binary tree - which the DB maintains for a specific column or composition of several columns. It means that searching for data goes from O(n) to O(logn) as the search now becomes a binary search.

The additional data structure must maintained on all **writes** including updates, so an index adds write latency but massively speeds up read latency. This is the core trade-off of adding an index, and it's why you can't just add indexes anywhere.



# What an index looks like
An index keeps a sorted list of entries which lead to a row reference, it's ordered so that can be B-searched. The row ref lets the computer jump straight to a disk location for that row.

### Simple index
A simple index on 'name' looks like:

**Branch nodes**
Store keys + pointers to child nodes
```
          ["Bob"]
         /       \
   [<= Bob]     [> Bob]
```

**Leaf nodes**
Store the actual data, ordered
```
Leaf 1:
("Alice", row_ref_1)
("Alice", row_ref_7)

Leaf 2:
("Bob",   row_ref_3)

Leaf 3:
("Charlie", row_ref_2)
("Charlie", row_ref_9)
```

### Composite index
Whereas a composite index like 'city', 'date' leaf nodes look like:
```
Leaf 1:
("new_york", "2024-01-01") → row_ref
("new_york", "2024-01-01") → row_ref

Leaf 2:
("new_york", "2024-01-02") → row_ref

Leaf 3:
("paris",    "2024-01-01") → row_ref
```


## Selectivity & cardinality (this is key)

(cardinality = uniqueness)
Indexes only help if they **reduce the search space meaningfully**.

- High cardinality (e.g. `user_id`) → great index
- Low cardinality (e.g. `is_active = true/false`) → often useless

Low-cardinality indexes can _hurt_ performance due to planner misestimation.