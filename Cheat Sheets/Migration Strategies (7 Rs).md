---
tags:
  - clf-c02
  - cheat-sheet
---
# Migration Strategies (7 Rs)

## The 7 Rs

| Strategy | Nickname | What changes | Example | Tooling hint |
| --- | --- | --- | --- | --- |
| **Retire** | Decommission | App is shut down | Unused app, no traffic in 90 days | Discovery data finds it |
| **Retain** | Revisit | Nothing; stays on premises for now | Recently upgraded, compliance or residency, mainframe | None |
| **Rehost** | Lift and shift | Nothing in the app; moves to EC2 | On-prem VMs to EC2 | AWS Application Migration Service |
| **Relocate** | Hypervisor-level lift and shift | Platform moves as-is to its cloud version | VMware to VMware Cloud on AWS | VMware tooling |
| **Repurchase** | Drop and shop | Replaced by a different product (usually SaaS) | On-prem CRM to SaaS CRM | Vendor migration |
| **Replatform** | Lift, tinker, and shift | Some optimization, same core architecture | Self-managed DB to Amazon RDS; app to Elastic Beanstalk; VMs to containers | AWS DMS for the database |
| **Refactor / re-architect** | Re-architect | Redesigned cloud-native | Monolith to microservices on Lambda and DynamoDB | Most complex and costly |

Memory aid by amount of change: **Retire, Retain** (no move) → **Relocate, Rehost** (move unchanged) → **Repurchase** (swap product) → **Replatform** (tweak) → **Refactor** (rebuild).

## Migration tools

| Need | Service |
| --- | --- |
| Inventory on-prem servers, utilization, dependencies | AWS Application Discovery Service |
| Single place to plan and track migrations | AWS Migration Hub |
| Lift-and-shift servers to EC2 with minimal downtime | AWS Application Migration Service |
| Move a database; source stays online; ongoing replication | AWS Database Migration Service (DMS) |
| Change database engine (Oracle to PostgreSQL) | AWS Schema Conversion Tool (SCT) + DMS |
| Terabytes to petabytes with slow or no network; edge compute | AWS Snow Family (Snowcone, Snowball Edge, Snowmobile up to 100 PB) |
| SFTP/FTPS/FTP file transfer into S3 or EFS | AWS Transfer Family |
| Business case and projected AWS cost | Migration Evaluator; AWS Pricing Calculator |
| Guidance and hands-on help | AWS Prescriptive Guidance, AWS Professional Services, AWS Partners, MAP |

Current status: AWS Migration Hub and AWS Application Discovery Service are no longer open to new customers (AWS points to AWS Transform), and AWS no longer offers Snow Family devices to new customers. The exam still tests all three.

## If the question says X, answer Y

- "Move without any changes", "lift and shift" → **Rehost**
- "Move to a managed database without changing the app's architecture" → **Replatform**
- "Rewrite as serverless / microservices" → **Refactor**
- "Replace with a SaaS product" → **Repurchase**
- "Keep on premises for now" → **Retain**; "shut it down" → **Retire**
- "Move VMware workloads to the cloud version of the same platform" → **Relocate**
- "Database migration with minimal downtime", "database replication" → **AWS DMS**
- "Heterogeneous database migration" → **AWS SCT + AWS DMS**
- "Petabytes, limited bandwidth", "remote site without connectivity" → **AWS Snow Family**
- "Exabyte-scale", "shipping container" → **Snowmobile**
- "Discover on-prem servers before migrating" → **Application Discovery Service**
- "Track migration progress in one place" → **Migration Hub**

Notes: [[1.3 Migration Strategies and AWS CAF]] · Services: [[Services - Migration and Transfer]] · Cards: [[Flashcards - Domain 1]]
