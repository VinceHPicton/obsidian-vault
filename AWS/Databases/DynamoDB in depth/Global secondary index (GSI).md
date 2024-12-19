An alternate entire copy of a table and all it's data, where a different field is used as the partition key.

You may include a subset of fields from the table in the GSI, or all of them.

Use case of this might be you have a load of purchases and you want to group that data by item number in the table, but also group it by warehouse in the GSI, letting you much more efficiently query all the orders from a particular warehouse.

![[Global secondary index (GSI) img.png]]

**GSI updates**
GSIs have *eventual consistency*, and so if you are writing to the table faster that the GSIs can update, table writes will be shut down so that the GSIs can catch up.

![[Global secondary index (GSI) updates.png]]