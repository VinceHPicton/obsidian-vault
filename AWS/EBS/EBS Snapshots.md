You can use an EBS snapshot to make a copy of an EBS volume at a point in time.
It is not necessary to detach the volume before you take a snapshot, but is recommended.
You can use a snapshot to "move" an EBS volume to another AZ/region, by doing a "copy" and then a "restore."
An EBS snapshot is located in a **specific region** where you made it (or copied it to)

**Key snapshot features**

- EBS snapshot archive: save 75% on costs by archiving a snapshot
- There is a recycle bin for ebs snapshots which you can figure retention policy for - 1 day to 1 year
- There is also Fast SnapShot Restore (FSR): normally snapshots are lazily loaded from S3, so there is a delay until the snapshot is ready to use, FSR means you can make them instantly available, but it's expensive. 