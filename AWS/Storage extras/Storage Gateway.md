The bridge between on-premises data and cloud data. The storage gateway appliance itself is deployed on-premises as a virtual machine, or you can buy a hardware appliance (more on this below).

![[Storage Gateway storage options.png]]
**Types of storage gateway**
- S3 file gateway
- FSx file gateway
- Volume gateway
- Tape gateway

**S3 file gateway**
- Can use [[NFS (Network File System) Protocol|NFS]] or [[SMB (Server Message Block) Protocol|SMB]] 
- Moving to glacier must be done via lifecycle policy.
- The most recently used data is cached locally on the file gateway
![[Storage Gateway s3.png]]

**FSx file gateway**
- Again locally caches frequently accessed data.
- Windows native compatibility (SMB, NTFS, AD).
- Automatically backed up to S3
![[Storage Gateway f gway.png]]

**Volume gateway**
- Block storage using [[iSCSI (Internet Small Computer Systems Interface) Protocol|iSCSI]] protocol - basically backup a full hard-drive
- Backed-up by point-in-time EBS snapshots to allow restores of on-prem volumes.
- **Cached volumes**: with this setting  most recent data is cached locally, bulk of the data is on S3
- **Stored volumes**: entire dataset is on-prem with scheduled backups to S3
![[Storage Gateway volume gway.png]]

**Tape gateway**
- Some companies use physical tapes to backup
- Tape gateway lets them do this to the cloud, storing virtual tapes on S3
- Tapes are stored in glacier
![[Storage Gateway tape gway.png]]

**Hardware appliance**
Bought on amazon.com, you can use this rather than run a VM on your on-prem system.
![[Storage Gateway hardw.png]]


**SUMMARY**
![[Storage Gateway summary.png]]