Allows you to edit S3 objects in some way using a lambda function, before the object gets to the requester.

For example:
- Converting XML to JSON
- Redacting personal info
- Watermarking images

Ontop of the bucket you create a standard [[S3 Access Points|S3 access point]] which the lambda queries, and also an **S3 object lambda access point** which the user requests from directly.

![[S3 Object Lambda im.png]]