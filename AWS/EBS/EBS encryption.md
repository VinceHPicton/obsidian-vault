Key fact: **EBS encryption utilises keys from [[KMS]] (AES-256)**

When you create an encrypted EBS volume you get:
- Data at rest encrypted
- In-flight data between instance and volume **is encrypted** - AWS handles the decryption behind the scenes
- All snapshots of volume encrypted
- All volumes created from that snapshot are encrypted

Encryption/decryption are handled automatically and have minimal latency impact.
If you copy an unencrypted snapshot you are able to encrypt it,
Snapshots of encrypted volumes are already encrypted.

How to encrypt an unencrypted EBS volume:
1. Create a snapshot of it
2. Encrypt the snapshot
3. Create new EBS volume from snapshot
4. Attach encrypted volume to instance.

You can also tick "encrypt this volume" to encrypt the volume from an unencrypted snapshot.