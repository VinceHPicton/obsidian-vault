Key management service - anytime you hear encryption is probably means this
You can audit key usage with CloudTrail
NEVER store keys in plaintext
Keys exist **in one region** and cant be passed around
Therefore to copy snapshots across regions they have to be reencrypted in the new region


There are **Symmetric** and **Asymmetric** keys -asym is keypairs like SSH

**Types of keys**
- AWS owned keys (free) - rotated once per year
- AWS managed key - rotated once per year
- Customer managed keys created in KMS $1/mo
- Customer managed imported to KMS $1/mo
You pay $0.03/10,000 calls to KMS

**Key policies**

These are similar to S3 bucket policies, but you cannot use the key at all without them
- The default key policy allows complete access to the key
- A custom key policy can define certain users with access.

**To share encrypted snapshots across accounts**
You must share the encrpyted snapshot, and then attach a key policy to the key used to encrypt it which allows the cross account to decrypt.
Then you can reencrypt in the new account with a key there.