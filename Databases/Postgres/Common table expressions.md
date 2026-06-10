A CTE is where you put a (`WITH ...`) into your query.

It can feed rows into subsequent CTEs. If a CTE returns no rows, anything selecting from it also gets no rows.