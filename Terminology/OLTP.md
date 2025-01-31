Online transaction processing is an approach to database systems which **prioritizes** speed in data **write** **operations**, it's intended for high volume transaction data without compromising data integrity.

Example use case would be an online retailer where stock needs to be immediately and accurately updated based on customer orders - if 2 customers order the last item an OLTP database system would ensure the first customer gets the order.

These systems are a primary use case of NoSQL databases.

The contrasting system is [[OLAP]] 