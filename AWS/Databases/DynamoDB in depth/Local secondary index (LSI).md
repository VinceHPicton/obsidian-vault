It's an **additional sort key**, allowing you to resort the data **within** a partition.

LSIs must **always** use the same partition key as the table, so it does not allow you regroup the data.

![[Local secondary index (LSI) img.png]]

An LSI must be defined at table creation, where you specify the sort key it will use, and which fields are going to copied into the rows of the LSI.

Because they're in the same partition they are *strongly consistent*.

The reason it says LSIs limit the number of range keys (**a synonym for sort keys**) is that there is a 10GB limit on 1 partition, and LSIs duplicate data, using up more of the partition.