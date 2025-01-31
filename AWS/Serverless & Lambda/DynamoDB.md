Key facts: 
- single-digit millisecond performance (<10 ms)
- DynamoDB is brilliant for a **rapidly evolving schema**

Other facts:
- It's fully managed, highly available with replication across AZs
- Scales to massive workloads
- Has standard and Infrequently accessed (IA) table tables

The database IS the service dynamoDB, you dont have to create a DB
It consists of tables:
- Each table has a primary key which must be decided at table creation
- Tables have infinite rows (items)
- **Item** **max size 400KB**
- Each item has attributes (nullable)
- Data types:
	- Scalar types = string, number etc
	- Document types = List, Map
	- Set types = number set, string set, etc
![[DynamoDB.png]]

**Capacity modes**

**Provisioned mode**
- Specify your estimate of reads/writes per second - you need to plan capacity ahead of time
- Pay for provisioned Read Capacity Units (RCU) & Write Capacity Units (WCU).
- Possible to add auto scaling mode for RCU/WCU

**On-Demand Mode**
- Scales automatically - no planning needed
- Pay only for what you use, but much more expensive (£££)
- Suitable for very unpredictable workloads, or workloads with tiny numbers of operations.