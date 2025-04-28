# Storage Architectures


🔹 DAS (Direct Attached Storage)

What it is:
Storage that is directly connected to a computer (like a hard drive or SSD connected via USB or SATA).

Key points:
	•	No network involved – it’s local to the machine.
	•	Fast access – since it’s directly attached.
	•	Limited sharing – typically used by one machine at a time.
	•	Examples: Internal HDD/SSD, external USB drives.

Use cases:
Good for single-server setups, personal computers, or simple backup solutions.



---


🔹 NAS (Network Attached Storage)

What it is:
A storage device connected to a network, accessible by multiple devices.

Key points:
	•	File-level storage – accessed using protocols like NFS, SMB/CIFS.
	•	Easy sharing – multiple users can access it over a network.
	•	Often comes with its own OS – with features like RAID, backups, etc.
	•	Examples: Synology, QNAP, or any Linux box serving files via NFS/SMB.

Use cases:
Great for small to medium businesses or home networks where file sharing and central storage are needed.

---


🔹 SAN (Storage Area Network)

What it is:
A dedicated high-speed network that provides block-level storage to servers.

Key points:
	•	Block-level storage – servers see it as a local disk (not a file share).
	•	High performance – uses protocols like iSCSI or Fibre Channel.
	•	Complex and expensive – often used in enterprise data centers.
	•	Highly scalable and redundant.

Use cases:
Enterprise environments needing high-performance storage for databases, VMs, or mission-critical apps.

---

| Feature             | DAS                     | NAS                        | SAN                        |
|---------------------|--------------------------|-----------------------------|-----------------------------|
| **Connection Type** | Direct (USB/SATA)        | Network (Ethernet)         | Dedicated storage network  |
| **Storage Level**   | Block                    | File                        | Block                       |
| **Shared Access**   | No                       | Yes                         | Yes                         |
| **Protocols**       | SCSI, SATA               | SMB, NFS                    | iSCSI, Fibre Channel        |
| **Cost**            | Low                      | Moderate                    | High                        |
| **Best For**        | Single machine, backup   | File sharing, backups       | High-performance workloads |

---

### Cloud Storage Types

- Object Storage
	- Amazon S3
	- Azure Block Storage
	
- File Storage
	- Amazon Elastic File System (EFS)
	- Azure File System

- Block Storage
	- Amazon EBS
	- Azure Disk Storage


Summary 

| Feature            | Block Storage          | File Storage            | Object Storage                  |
|--------------------|------------------------|--------------------------|----------------------------------|
| Data Structure     | Blocks (raw chunks)    | Files & folders          | Objects (data + metadata + ID)  |
| Access Method      | Via OS (mount as disk) | Via protocols (NFS/SMB)  | Via APIs (HTTP/S3)              |
| Performance        | Very high              | Moderate                 | Depends, but highly scalable    |
| Scalability        | Moderate               | Limited by filesystem    | Very high (cloud-native)        |
| Metadata Support   | Minimal                | Basic (filename, etc.)   | Extensive (custom metadata)     |
| Use Cases          | Databases, VMs         | Team file shares         | Cloud storage, backups, media   |



