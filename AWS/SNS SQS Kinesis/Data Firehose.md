A fully managed, serverless, near real-time data streaming service used to load data into data lakes, data warehouses, and analytics services.
- It's nearly real-time because fills up it's buffer (customizable size, eg 5 MiB) before processing.
- Allows processing data with a lambda before sending on to consumers.

*previously called kinesis firehose*
"**Near real-time**" in exa usually points to data firehose

![[Data Firehose.png]]
NB: Each record from producer is up to 1MB

**REMEMBER FOR EXAM**
- Important source: [[Kinesis Data Streams|kinsesis data stream]]
- Important destinations:
	- S3
	- Redshift
	- Opensearch
	- Custom HTTP endpoint
- Remember that 3rd party options also exist
- Can convert data formats




![[Data Firehose2.png]]