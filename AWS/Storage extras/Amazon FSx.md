FSx is for running high-performance custom file systems on the cloud.
FSx means "File System x" where the x means any type, like a variable.

There are 4 to know about:
- FSx for Windows (file server)
- FSx for Lustre (linux cluster)
- FSx for NetApp ONTAP
- FSx for OpenZFS


**FSx for Windows**
Windows file system share drive
- Supports SMB protocol and windows NTFS
- MS active directory
- **Count be mounted onto Linux EC2 instances**
- Supports **MS distributed file system (DFS) namespaces** - groups files across multiple file systems
- Storage options
	- SSD
	- HDD


**FSx for Lustre**
Lustre is a type of parallel distributed file system, for large-scale computing
- Key use case to look out for is **high-performance computing (HPC)**
- Other key point is **seamless integration with S3**
	- "read S3" as filesystem
	- write output to S3


**Deployment options for FSx**
The choices are Scratch and Persistent filesystems

**Scratch**: Temp storage, cheaper, can burst for faster CPU, data gone if server dies
**Persistent**: data replicated across AZ, for long term storage.


**FSx NetApp ONTAP and OpenZFS**
To remember: **Both good for point-in-time instantaneous cloning** 

Other than that they're the same
![[Amazon FSx 1.png]]