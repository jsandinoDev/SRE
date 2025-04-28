# Storage Basics

Types of access protocol

- SAN (Storage area network)

- NAS (Network attached storage)

---

## NAS

- File leve access storage resources

- Remote Storage System


Protocols

- SMB/CIFS 
	- Server message block -> IBM
	- Common internet file system -> microsoft

- NFS
	- Common used for VMFS in VMWare
	- Servers "exports" clients "mount"


---

## SAN

- Block levet access
- Manage space on storage system
- Management of files resides with the client
- Separate networks
- used mosttly for servers


Protocols

- FC (fibre channel)

- LUN 
	- Logical Unit Number 
	- Disk that will be presented to a host

	- Client -> iniciador
	- Storage system -> Target

---

## Object Storage

- Organize into containers
- Flexible size
- Buckets or containers
- BUckets can spam multiple node and greographic location





---

### RAID

Redundancy array of inexpensive/independant disks

**Types**
For visual view notebook

- 0
  - se distribuye en ambos discos
  - (+) performance
  - (-) reliability
- 1
  - (-) performance
  - (+) reliability
  - se hace espejo (A1, A2)
- 4

  - block level
  - (+) performance
  - (+) reliablity
  - 3re disco para revisar

- 5

  - similar al anterior pero una copia en cada disco

- 6

  - lo mismo pero con 2 respaldos por disco

- Hybrid
  - Se combinan varios tipos, ex. tree
