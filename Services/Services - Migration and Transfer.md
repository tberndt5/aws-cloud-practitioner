---
tags:
  - clf-c02
  - services
  - services/migration-and-transfer
category: "Migration and Transfer"
status: not-started
---
# Services: Migration and Transfer

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Migration strategies (the 7 Rs), the AWS Cloud Adoption Framework, and when to use database replication or Snowball are taught in [[1.3 Migration Strategies and AWS CAF]]; database migration tools also appear in [[3.4 Database Services]]. One-page summary: [[Migration Strategies (7 Rs)]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#AWS Application Discovery Service]] | Collects on-premises server data to plan migration | "Discover", "inventory on-premises servers", "dependencies", "utilization data to plan" |
| [[#AWS Application Migration Service]] | Automated lift-and-shift (rehost) of servers | "Lift and shift", "rehost", "minimal downtime server migration" |
| [[#AWS Database Migration Service (AWS DMS)]] | Migrates databases with source staying online | "Migrate a database", "minimal downtime", "continuous replication" |
| [[#AWS Migration Hub]] | Single place to track migration progress | "Track status of migrations", "central dashboard", "across multiple tools" |
| [[#AWS Schema Conversion Tool (AWS SCT)]] | Converts schema between different database engines | "Different engine", "Oracle to Aurora", "heterogeneous", "convert schema/stored procedures" |
| [[#AWS Snow Family]] | Physical devices for offline transfer and edge compute | "Petabytes", "limited or no bandwidth", "remote location", "ship data" |
| [[#AWS Transfer Family]] | Managed SFTP/FTPS/FTP into S3 or EFS | "SFTP", "FTP", "partners upload files", "keep existing file-transfer clients" |

> [!tip] Migration flow
> **Discover** (Application Discovery Service) → **Plan and track** (Migration Hub) → **Move servers** (Application Migration Service) / **move databases** (SCT converts the schema if engines differ, then DMS moves the data) / **move bulk data offline** (Snow Family) / **move files over SFTP** (Transfer Family).

## AWS Application Discovery Service

> [!summary] Collects usage and configuration data about on-premises servers and databases to help plan a migration to AWS.

- **What it does:** Gathers information about on-premises servers: configuration, performance and utilization, running processes, and network connections between systems (dependencies). The data helps estimate cost and group servers into applications for migration planning.
- **Choose it when:** A company is at the start of a migration and needs to inventory its data center and understand server dependencies before moving.
- **Key facts:**
  - Discovery happens ==before== migration (planning phase).
  - Agent-based collection (installed on servers) or agentless collection (for VMware VMs).
  - Results are viewed in [[#AWS Migration Hub]] and can be exported for analysis.
  - Data is encrypted in transit and at rest.
- **Don't confuse with:** [[#AWS Application Migration Service]] (actually moves the servers) and [[#AWS Migration Hub]] (tracks progress and shows discovered data).
- **Docs:** [What is AWS Application Discovery Service?](https://docs.aws.amazon.com/application-discovery/latest/userguide/what-is-appdiscovery.html)

Current status: AWS Application Discovery Service closed to new customers on November 7, 2025; AWS recommends AWS Transform for discovery and assessment.

## AWS Application Migration Service

> [!summary] Automated lift-and-shift (rehost) solution for migrations to AWS.

- **What it does:** Continuously replicates source servers (physical, virtual, or in another cloud) at the block level into a staging area in your AWS account, then launches them as EC2 instances when you cut over. Applications run on AWS without code changes.
- **Choose it when:** The scenario says lift-and-shift, rehost, or move servers to AWS quickly with minimal downtime and without re-architecting.
- **Key facts:**
  - The recommended AWS service for ==rehost== migrations.
  - Continuous block-level replication keeps cutover windows short (minutes).
  - Supports non-disruptive test launches before cutover.
  - Source can be on-premises physical servers, VMware, Hyper-V, or other clouds.
  - Replaced CloudEndure Migration and AWS Server Migration Service (SMS fully shut down April 1, 2023).
- **Don't confuse with:** [[Services - Storage#AWS Elastic Disaster Recovery|AWS Elastic Disaster Recovery]] (same replication technology, but for disaster recovery rather than one-time migration) and [[#AWS Database Migration Service (AWS DMS)]] (databases, not whole servers).
- **Docs:** [What is AWS Application Migration Service?](https://docs.aws.amazon.com/mgn/latest/ug/what-is-application-migration-service.html)

## AWS Database Migration Service (AWS DMS)

> [!summary] Migrate relational databases, data warehouses, NoSQL databases, and data stores to AWS.

- **What it does:** Moves data from a source database to a target database on AWS. The ==source database remains fully operational== during migration, and ongoing replication (change data capture) keeps the target in sync until cutover, which minimizes downtime.
- **Choose it when:** The question asks to migrate a database to AWS with minimal downtime, or to continuously replicate data between databases.
- **Key facts:**
  - Homogeneous migrations (same engine, for example Oracle to Oracle) and heterogeneous migrations (different engines, for example Oracle to Amazon Aurora).
  - For heterogeneous migrations, convert the schema first with [[#AWS Schema Conversion Tool (AWS SCT)]].
  - Sources and targets can be on premises, on EC2, or AWS managed databases (RDS, Aurora, DynamoDB, Redshift, S3, and others).
  - Supports continuous replication, which is the "database replication" strategy named in exam guide 1.3.
- **Don't confuse with:** [[#AWS Schema Conversion Tool (AWS SCT)]] (converts structure; DMS moves the data) and [[#AWS Application Migration Service]] (moves whole servers).
- **Docs:** [What is AWS Database Migration Service?](https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html)

## AWS Migration Hub

> [!summary] A central location to discover existing servers, plan migrations, and track the status of each application migration.

- **What it does:** A single console that shows migration status across multiple AWS and partner migration tools. It also displays discovery data and can provide EC2 instance and modernization recommendations.
- **Choose it when:** The question asks for one place to track the progress of migrations across many applications or tools.
- **Key facts:**
  - ==Tracking and visibility==; it does not itself move servers or data.
  - Integrates with Application Discovery Service, Application Migration Service, and DMS.
  - Groups servers into applications to track each application's migration.
  - No additional charge; you pay for the migration tools you use.
- **Don't confuse with:** [[#AWS Application Discovery Service]] (collects the inventory data) and [[#AWS Application Migration Service]] (does the move).
- **Docs:** [What is AWS Migration Hub?](https://docs.aws.amazon.com/migrationhub/latest/ug/whatishub.html)

Current status: AWS Migration Hub stopped accepting new customers on November 7, 2025; AWS recommends AWS Transform, which provides equivalent capabilities.

## AWS Schema Conversion Tool (AWS SCT)

> [!summary] Convert an existing database schema from one database engine to another.

- **What it does:** Converts a source database's schema (tables, indexes, views) and code objects (stored procedures, functions) into a format compatible with a different target engine. It reports what it cannot convert automatically so you can fix it manually.
- **Choose it when:** The migration is ==heterogeneous== (different source and target engines), such as Oracle or SQL Server to Amazon Aurora PostgreSQL, or a data warehouse to Amazon Redshift.
- **Key facts:**
  - Needed only when the engines differ; not needed for same-engine migrations.
  - Downloadable application you run on your own computer.
  - Used with [[#AWS Database Migration Service (AWS DMS)]], which then moves the data.
  - Produces an assessment report showing conversion effort.
- **Don't confuse with:** [[#AWS Database Migration Service (AWS DMS)]], which moves data. Remember: SCT = Schema, DMS = Data.
- **Docs:** [What is the AWS Schema Conversion Tool?](https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/CHAP_Welcome.html)

## AWS Snow Family

> [!summary] Run operations in remote, non-data center environments, and locations without network connectivity.

- **What it does:** Rugged, secure physical devices that AWS ships to you. You load data locally (or run compute at the edge), ship the device back, and AWS imports the data into Amazon S3. They solve two problems: moving very large data sets when network transfer would take too long, and computing where there is little or no connectivity.
- **Choose it when:** The question mentions terabytes to petabytes of data with limited bandwidth, a remote or disconnected site (ship, mine, field location, military), or the exam guide's "use of AWS Snowball" as a migration strategy.
- **Key facts:** the device lineup as the exam knows it, then the tested specifics.

| Device | Usable storage | Compute | Use it for |
| --- | --- | --- | --- |
| **Snowcone** | 8 TB HDD, or 14 TB on Snowcone SSD | Small (2 vCPU class) | Smallest, portable device for edge sites and small transfers |
| **Snowball Edge Storage Optimized** | 80 TB (newer model: 210 TB NVMe) | Moderate (newer model: 104 vCPU, 416 GB) | Large-scale data migration and local storage |
| **Snowball Edge Compute Optimized** | 28 TB NVMe on the current model | Most compute: up to 104 vCPU, 416 GB memory; GPU option on earlier models | Edge computing: ML inference, video analysis in disconnected environments |
| **Snowmobile** | Up to ==100 PB== per unit | None | Exabyte-scale data center moves; a 45-foot shipping container pulled by a truck |

- ==Data is encrypted== with keys managed in AWS KMS; keys are never stored on the device. Devices are tamper-resistant.
- Snowball Edge devices can run EC2-compatible instances and Lambda functions locally, and can be clustered (3 to 16 devices) for durable local storage.
- Picking a device: tens of petabytes or more from one data center points to Snowmobile; a small, portable edge device points to Snowcone; terabytes to a few petabytes (using several devices) points to Snowball Edge.
- Pricing: a service fee per job plus per-day charges; data transfer into AWS is free.
- **Don't confuse with:** [[Services - Storage#AWS Storage Gateway|AWS Storage Gateway]] (ongoing hybrid access to cloud storage over the network), AWS DataSync (online transfer over the network), [[Services - Networking and Content Delivery#AWS Direct Connect|AWS Direct Connect]] (dedicated network link, takes weeks to set up), and [[Services - Compute#AWS Outposts|AWS Outposts]] (permanent AWS racks in your data center).
- **Docs:** [What is AWS Snowball Edge?](https://docs.aws.amazon.com/snowball/latest/developer-guide/whatisedge.html)

Current status: AWS Snowmobile reached end of support on March 14, 2024 and Snowcone was discontinued on November 12, 2024; AWS Snowball Edge is no longer available to new customers, and AWS points new customers to AWS DataSync, AWS Data Transfer Terminal, or AWS Outposts.

## AWS Transfer Family

> [!summary] Transfer files in to and out of AWS storage services.

- **What it does:** A fully managed file transfer service that supports SFTP, FTPS, FTP, and AS2 protocols, storing files directly in Amazon S3 or Amazon EFS. Partners and users keep using their existing file-transfer clients and workflows.
- **Choose it when:** A company has partners or systems that exchange files over SFTP or FTP and wants to move that workload to AWS without running its own file-transfer servers.
- **Key facts:**
  - Protocols: ==SFTP, FTPS, FTP, AS2==.
  - Storage back ends: Amazon S3 and Amazon EFS.
  - Authenticate users with service-managed users, Active Directory, or a custom identity provider.
  - No servers to manage; pay per protocol-hour enabled and per GB transferred.
- **Don't confuse with:** [[#AWS Snow Family]] (offline bulk transfer on physical devices), AWS DataSync (scheduled bulk online copies between storage systems), and [[Services - Storage#AWS Storage Gateway|AWS Storage Gateway]] (hybrid storage access through NFS, SMB, or iSCSI).
- **Docs:** [What is AWS Transfer Family?](https://docs.aws.amazon.com/transfer/latest/userguide/what-is-aws-transfer-family.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
