---
tags:
  - clf-c02
  - cheat-sheet
---
# Storage Picker

Back to: [[3.6 Storage Services]] · Related: [[S3 Storage Classes]], [[Database Picker]], [[Compute Picker]]

## Step 1: which storage type?

| Type | Access | AWS service | Shared by many? | Scope |
|---|---|---|---|---|
| Object | HTTPS API, whole objects | Amazon S3 | Yes (over the API) | Regional (≥3 AZs, except One Zone classes) |
| Block | Mounted disk, OS formats it | Amazon EBS | Usually one instance | **One AZ** |
| Block (temporary) | Local disk on the host | EC2 instance store | One instance | Host only, **ephemeral** |
| File (Linux, NFS) | Network file share | Amazon EFS | Thousands of instances | Multi-AZ (or One Zone) |
| File (Windows, SMB, AD) | Network file share | FSx for Windows File Server | Yes | Single- or Multi-AZ |
| File (HPC) | Parallel file system | FSx for Lustre | Yes, compute clusters | — |
| File (existing NetApp / ZFS) | NFS, SMB, iSCSI | FSx for NetApp ONTAP / OpenZFS | Yes | — |

## Step 2: special needs

| Need | Service |
|---|---|
| On-premises apps use cloud storage with a **local cache** | AWS Storage Gateway |
| … as file shares (NFS/SMB) landing in S3 | S3 File Gateway |
| … as iSCSI block volumes (cached or stored mode) | Volume Gateway |
| … as virtual tapes for existing backup software | Tape Gateway |
| Central, policy-based backups across EBS, EFS, RDS, DynamoDB, FSx, S3, on-premises VMware | AWS Backup |
| Continuous server replication, recover in minutes | AWS Elastic Disaster Recovery |
| Move petabytes offline or compute at a disconnected site | AWS Snow Family |
| Online bulk transfer of files to S3, EFS, FSx | AWS DataSync |
| SFTP/FTPS/FTP into S3 or EFS | AWS Transfer Family |

## EBS vs instance store

| | EBS | Instance store |
|---|---|---|
| Persistence | Survives stop/start | Lost on stop, hibernate, terminate; survives reboot |
| Location | Network-attached, one AZ | Physically attached to the host |
| Backup | Snapshots (incremental, stored in S3, copy across Regions) | None built in |
| Types | SSD (gp2/gp3, io1/io2) for IOPS and boot; HDD (st1, sc1) for throughput, cannot boot | Fixed by instance type |
| Use | Boot volumes, databases | Cache, buffer, scratch data |

## If the question says X, answer Y

- "Unlimited storage for images, videos, backups, data lake" → S3
- "Host a static website" → S3 (plus CloudFront)
- "Boot volume", "database on EC2", "persistent block storage" → EBS
- "Temporary", "scratch", "highest I/O, data can be lost" → instance store
- "Shared file system for Linux instances across AZs" → EFS
- "Windows file share with Active Directory" → FSx for Windows File Server
- "High-performance computing", "ML training at hundreds of GB/s" → FSx for Lustre
- "Hybrid", "on-premises access to cloud storage", "local cache" → Storage Gateway
- "Replace physical tape library" → Tape Gateway
- "Centralize and automate backups" → AWS Backup
- "Recover on-premises servers into AWS within minutes" → Elastic Disaster Recovery
- "Limited bandwidth, petabytes to move" → Snow Family
