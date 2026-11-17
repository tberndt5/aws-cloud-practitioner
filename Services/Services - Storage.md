---
tags:
  - clf-c02
  - services
  - services/storage
category: "Storage"
status: not-started
---
# Services: Storage

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Concepts (object versus block versus file storage, storage classes, lifecycle policies, hybrid and cached storage, backup) are taught in [[3.6 Storage Services]]; storage pricing is in [[4.1 AWS Pricing Models]]. Quick-reference tables: [[S3 Storage Classes]] and [[Storage Picker]].

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#AWS Backup\|AWS Backup]] | Central, policy-based backups across AWS services | "centrally manage backups", "backup policy across services/accounts" |
| [[#Amazon Elastic Block Store (Amazon EBS)\|Amazon EBS]] | Persistent block volumes for one EC2 instance | "boot volume", "block storage", "database on EC2", "persists after stop" |
| [[#Amazon Elastic File System (Amazon EFS)\|Amazon EFS]] | Serverless shared NFS file system for Linux | "shared file system", "many Linux instances", "NFS", "across AZs" |
| [[#AWS Elastic Disaster Recovery\|AWS Elastic Disaster Recovery]] | Continuous server replication for fast recovery into AWS | "disaster recovery for on-premises servers", "RPO seconds, RTO minutes" |
| [[#Amazon FSx\|Amazon FSx]] | Managed third-party file systems (Windows, Lustre, ONTAP, OpenZFS) | "Windows file shares/SMB", "Active Directory", "Lustre/HPC" |
| [[#Amazon S3\|Amazon S3]] | Scalable object storage in buckets | "objects", "static website", "data lake", "unlimited storage", "11 nines" |
| [[#Amazon S3 Glacier\|Amazon S3 Glacier]] | Low-cost archive storage classes within S3 | "archive", "long-term retention", "rarely accessed", "compliance records" |
| [[#AWS Storage Gateway\|AWS Storage Gateway]] | Hybrid bridge from on premises to AWS storage | "on-premises apps use cloud storage", "local cache", "replace tape" |

> [!tip] Object, block, file
> **Object** (S3, Glacier): whole files with metadata, accessed over HTTP APIs, virtually unlimited. **Block** (EBS, instance store): raw disk volumes attached to an instance, like a hard drive. **File** (EFS, FSx): shared folders that many servers mount at once. **Hybrid/cached** (Storage Gateway): on-premises access to cloud storage.

## AWS Backup

> [!summary] Centralize and automate backups of data from AWS storage services and on-premises storage systems.

- **What it does:** AWS Backup is a fully managed, policy-based backup service. You create a backup plan (how often to back up, how long to keep backups, where to copy them) and assign resources to it; AWS Backup then runs and tracks backups across many services from one console.
- **Choose it when:** the question says "centrally manage and automate backups", "one backup policy for EC2, EBS, RDS, DynamoDB, EFS, and S3", "backups across accounts in an organization", or "meet backup compliance requirements".
- **Key facts:**
  - Supports services such as EC2, EBS, EFS, FSx, RDS, Aurora, DynamoDB, S3, Storage Gateway, and on-premises VMware.
  - Backup plans define schedule, retention, and lifecycle (move older backups to cold storage).
  - Cross-Region and cross-account backup copies; integrates with AWS Organizations for organization-wide policies.
  - **AWS Backup Vault Lock** makes backups immutable (write once, read many) for compliance; **AWS Backup Audit Manager** reports on backup compliance.
- **Don't confuse with:** **Elastic Disaster Recovery** (continuous replication for fast failover of whole servers; Backup is point-in-time copies for restore). **EBS snapshots/RDS automated backups** (per-service features; AWS Backup manages them centrally). **Storage Gateway Tape Gateway** (replaces physical tape for existing backup software).
- **Docs:** [What is AWS Backup?](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html)

## Amazon Elastic Block Store (Amazon EBS)

> [!summary] Block-level storage volumes for use with EC2 instances.

- **What it does:** EBS provides network-attached block storage volumes (virtual hard drives) for EC2 instances. Data on an EBS volume persists independently of the instance: it survives stopping the instance and can be detached and attached to another instance in the same Availability Zone.
- **Choose it when:** the question needs a boot volume, persistent block storage for one EC2 instance, a database or application installed on EC2, or low-latency disk for a single server.
- **Key facts:**
  - ==An EBS volume lives in one Availability Zone== and attaches to instances in that AZ (generally one instance at a time; Multi-Attach is a limited exception).
  - **Snapshots** are point-in-time, incremental backups stored in S3; they can be copied to other Regions and used to create new volumes.
  - Volume types: SSD-backed (General Purpose gp2/gp3, Provisioned IOPS io1/io2) and HDD-backed (Throughput Optimized st1, Cold sc1).
  - Encryption at rest with AWS KMS keys.
  - **Instance store** is the other block option: disks physically attached to the host, very fast but ==temporary== — data is lost when the instance stops, hibernates, or terminates. Use it for caches, buffers, and scratch data.
- **Don't confuse with:** **EFS** (shared file system mounted by many instances across AZs). **S3** (object storage accessed over HTTP, not a disk). **Instance store** (ephemeral).
- **Docs:** [What is Amazon EBS?](https://docs.aws.amazon.com/ebs/latest/userguide/what-is-ebs.html)

## Amazon Elastic File System (Amazon EFS)

> [!summary] Serverless, fully scalable shared file system.

- **What it does:** EFS is a fully managed file system that many compute resources (EC2 instances, containers, Lambda functions) can mount and use at the same time over the NFS protocol. It grows and shrinks automatically as files are added and removed, so you never provision capacity.
- **Choose it when:** the question says "shared file storage for multiple Linux EC2 instances", "NFS", "file system that scales automatically", "content management or web serving across many servers", or "file system available across AZs".
- **Key facts:**
  - ==Linux workloads, NFS protocol==; Windows instances are not supported (use FSx for Windows File Server).
  - Regional file systems store data across multiple AZs; One Zone file systems use a single AZ at lower cost.
  - Elastic: pay for storage used, no capacity planning.
  - Storage classes (Standard, Infrequent Access, Archive) with lifecycle management move rarely used files to cheaper classes automatically.
- **Don't confuse with:** **EBS** (block volume for one instance in one AZ). **FSx for Windows File Server** (SMB shares for Windows). **S3** (object storage, not a mountable file system).
- **Docs:** [What is Amazon EFS?](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)

## AWS Elastic Disaster Recovery

> [!summary] Minimizes downtime and data loss from natural catastrophes, application failures, or disruptions of service.

- **What it does:** Elastic Disaster Recovery (AWS DRS) continuously replicates on-premises or cloud-based servers into a low-cost staging area in your AWS account. When disaster strikes, you launch fully provisioned recovery instances on AWS within minutes, from the latest state or an earlier point in time, then fail back when the primary site is restored.
- **Choose it when:** the question says "disaster recovery for on-premises servers to AWS", "minimize downtime and data loss", "recover in minutes", "RPO of seconds", or "recover from ransomware using a previous point in time".
- **Key facts:**
  - AWS states it enables ==RPOs of seconds and RTOs of minutes== (RPO, recovery point objective = acceptable data loss; RTO, recovery time objective = acceptable downtime).
  - Staging area uses affordable storage and minimal compute, so you avoid paying for a full idle duplicate site.
  - Supports non-disruptive recovery and failback drills.
  - Successor to CloudEndure Disaster Recovery.
- **Don't confuse with:** **AWS Backup** (scheduled point-in-time backups, slower restore). **AWS Application Migration Service** (one-time lift-and-shift migration using similar replication; DRS is ongoing protection). **Multi-AZ RDS** (database high availability inside AWS).
- **Docs:** [What is Elastic Disaster Recovery?](https://docs.aws.amazon.com/drs/latest/userguide/what-is-drs.html)

## Amazon FSx

> [!summary] Launch, run, and scale file systems in the cloud.

- **What it does:** FSx provides fully managed file systems built on popular commercial and open-source file systems, so applications that expect those specific features can move to AWS without changes. AWS handles hardware, patching, and backups.
- **Choose it when:** the question mentions Windows file shares, SMB, Active Directory integration, Microsoft applications, high-performance computing (HPC), Lustre, NetApp, or OpenZFS.
- **Key facts:**
  - ==**FSx for Windows File Server**==: native Windows file system over SMB, integrates with Microsoft Active Directory; the answer for Windows shared storage.
  - ==**FSx for Lustre**==: high-performance file system for HPC, ML, and media processing; can link to an S3 bucket.
  - **FSx for NetApp ONTAP** and **FSx for OpenZFS**: managed versions of those file systems for migrating existing NAS workloads.
  - Named in task statement 3.6 as a file service.
- **Don't confuse with:** **EFS** (Linux NFS, serverless, no specific third-party file system). **Storage Gateway** (gives on-premises users access to cloud storage). **EBS** (block storage for one instance).
- **Docs:** [Amazon FSx](https://aws.amazon.com/fsx/)

## Amazon S3

> [!summary] Scalable object storage in the cloud.

- **What it does:** Amazon Simple Storage Service (S3) stores any amount of data as objects (a file plus metadata) inside buckets, accessed over the web through APIs, the console, or the CLI. It underpins backups, data lakes, static website hosting, application assets, and log storage.
- **Choose it when:** the question says "store objects/files at virtually unlimited scale", "static website", "data lake", "backup and archive", "durable storage for images and videos", or "store logs".
- **Key facts:**
  - ==Designed for 99.999999999% (11 nines) durability== for all storage classes; Standard is designed for 99.99% availability.
  - Bucket names are globally unique; buckets live in one Region (you choose it); individual objects up to 5 TB.
  - Storage classes: Standard, Intelligent-Tiering (moves data between tiers automatically based on access), Standard-IA, One Zone-IA, the Glacier classes, and Express One Zone. See [[S3 Storage Classes]].
  - ==**Lifecycle policies**== automatically transition objects to cheaper storage classes after a set number of days, or expire (delete) them; use them when access drops predictably over time (for example logs moved to Standard-IA after 30 days, Glacier after 90, deleted after 7 years).
  - Security: buckets are private by default; Block Public Access, bucket policies, IAM; new objects are encrypted at rest by default (SSE-S3). Versioning protects against accidental overwrite or deletion.
  - Replication (cross-Region or same-Region) copies objects to another bucket automatically.
- **Don't confuse with:** **EBS** (block disk for one EC2 instance). **EFS** (mountable shared file system). **S3 Glacier storage classes** (archive tiers inside S3). **CloudFront** (caches S3 content at edge locations).
- **Docs:** [What is Amazon S3?](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)

## Amazon S3 Glacier

> [!summary] Secure and durable data archiving and long-term backup (reference guide: "Amazon S3 Glacier storage classes").

- **What it does:** The S3 Glacier storage classes are the low-cost archive tiers of Amazon S3. You trade retrieval speed and a minimum storage duration for much lower storage prices, making them suited to backups, compliance records, and media archives that are rarely read.
- **Choose it when:** the question says "archive", "long-term retention for compliance", "rarely accessed", "lowest-cost storage", "replace tape archives", or names a retrieval time (milliseconds, minutes to hours, within 12 hours).
- **Key facts:**
  - **S3 Glacier Instant Retrieval:** millisecond retrieval; 90-day minimum storage duration; for archives accessed about once a quarter that still need immediate access.
  - **S3 Glacier Flexible Retrieval:** expedited 1–5 minutes, standard 3–5 hours, bulk 5–12 hours (bulk retrievals are free); 90-day minimum; for backups and DR data accessed once or twice a year.
  - **S3 Glacier Deep Archive:** standard retrieval within 12 hours, bulk within 48 hours; 180-day minimum; ==the lowest-cost storage in AWS==, for multi-year compliance retention.
  - Same 11 nines durability as S3 Standard; objects are moved there by lifecycle policy or written directly.
  - Flexible Retrieval and Deep Archive are archival: you must restore an object before reading it.
  - S3 Glacier Flexible Retrieval was formerly called "S3 Glacier".
  - Current status: the original standalone, vault-based Amazon Glacier service (separate from the S3 storage classes) stopped accepting new customers on December 15, 2025; AWS recommends the S3 Glacier storage classes.
- **Don't confuse with:** **S3 Standard-IA** (infrequent access, millisecond retrieval, 30-day minimum, not an archive class). **AWS Backup** (manages backups; can store them in cold storage). **Storage Gateway Tape Gateway** (presents virtual tapes on premises that archive to Glacier classes).
- **Docs:** [Understanding S3 Glacier storage classes](https://docs.aws.amazon.com/AmazonS3/latest/userguide/glacier-storage-classes.html)

## AWS Storage Gateway

> [!summary] Connect an on-premises software appliance with cloud-based storage.

- **What it does:** Storage Gateway is a hybrid cloud storage service. You run a gateway (a virtual machine or hardware appliance) in your data center; on-premises applications talk to it using standard file, block, or tape protocols, while it stores the data in AWS (S3, Glacier classes, EBS snapshots) and keeps a local cache of frequently used data for low-latency access.
- **Choose it when:** the question says "on-premises applications need access to cloud storage", "hybrid storage", "cached file system", "low-latency local access to data stored in AWS", "replace physical tape backups", or "extend on-premises storage to AWS".
- **Key facts:**
  - **S3 File Gateway:** NFS/SMB file shares on premises, stored as objects in S3.
  - **Volume Gateway:** iSCSI block volumes; cached mode keeps primary data in AWS with a local cache, stored mode keeps all data locally with asynchronous backup to AWS as EBS snapshots.
  - **Tape Gateway:** virtual tape library for existing backup software; archives to S3 Glacier Flexible Retrieval or Deep Archive.
  - **FSx File Gateway:** on-premises cached access to FSx for Windows File Server. Current status: no longer available to new customers (since October 28, 2024); existing customers can keep using it.
  - Named in task statement 3.6 as the example of ==cached file systems==.
- **Don't confuse with:** **Snow Family** (physical devices to ship large data sets offline). **DataSync/Transfer Family** (move or transfer data; not an ongoing local cache). **Outposts** (runs AWS compute on premises). **Direct Connect** (network link, not storage).
- **Docs:** [AWS Storage Gateway](https://aws.amazon.com/storagegateway/)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
