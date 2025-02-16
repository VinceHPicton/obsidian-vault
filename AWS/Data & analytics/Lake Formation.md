Data lake service in aws
A data lake = a central place where you store all your data for processing/analysis

You can combine structured and unstructured data in it (data in data lake is in its own S3).

- **Use out of the box blue-prints** for S3, RDS, relational and nosql data
- Get fine-grained access control of your apps - control access to individual row and columns.

**Key use case: centralised permissions**
By ingesting data from all different sources to lake formation you can from there control access to it, rather than setting up controls on all different services.

![[Lake Formation.png]]