It's possible to replicate a KMS key to other regions, if you do this there will always be one **primary** key, and 1+ **replicas** in other regions.
They will have the **same key ID** but different ARNs.

It's generally not recommended to do this except in specific use cases.


**Use case 1: a global DynamoDB table with a client-side encrypted attribute**
If your DynamoDB table has a field like bank card number which needs to be encrypted, that encrypted field will be replicated to the other regions.
So if the other region was across the entire world, there would be a long latency to request the KMS key in the primary region, therefore you use a multi-region key to store the needed key in both places.
![[KMS multi-region keys.png|350]]

**Use case 2: This exact same problem can apply to an encrypted column in global aurora**