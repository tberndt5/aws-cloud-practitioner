---
tags:
  - clf-c02
  - cheat-sheet
---
# Shared Responsibility Model

**AWS = security OF the cloud** (what you cannot touch). **Customer = security IN the cloud** (what you create or configure). The more managed the service, the more AWS does. Data and IAM are **always** the customer's.

## The reference guide lists (memorize)

| AWS | Customer | Shared |
| --- | --- | --- |
| Global infrastructure | Client-side data integrity and encryption | Patches |
| Hosts | Manage guest OS | Configuration |
| Operation and virtualization of software | Set password policies | Training and awareness |
| Hardware maintenance | Configure firewalls and networks | |
| Physical and environmental controls | Encrypt client-side data | |
| Edge location management | Configure IAM roles | |
| Secure the EC2 hypervisor | Patch OS of EC2 instances | |
| Patch OS of RDS instances | Determine which services have access to DynamoDB tables | |
| Patch ELBs | | |
| Patch OS used by Lambda | | |
| Server-side encryption in Amazon S3 | | |

## Control types

| Type | Meaning | Example |
| --- | --- | --- |
| Inherited | Customer fully inherits from AWS | Physical and environmental controls |
| Shared | Each side does its own layer | Patch management, configuration management, awareness and training |
| Customer-specific | Customer only | Service and communications protection, zone security |

## How it shifts by service

| Task | EC2 (IaaS) | RDS (managed) | Lambda (serverless) |
| --- | --- | --- | --- |
| Physical, hardware, hypervisor | AWS | AWS | AWS |
| OS patching | **Customer** | AWS | AWS |
| DB engine / runtime patching | Customer | AWS | AWS |
| Code, schema, function | Customer | Customer | Customer |
| Security groups / NACLs | Customer | Customer | Customer (if in VPC) |
| IAM, data, encryption choices | Customer | Customer | Customer |

Ladder: on-premises → EC2 (you start at guest OS) → RDS (you start at DB settings) → Lambda, S3, DynamoDB (you start at code, data, permissions).

## If the question says X, answer Y

- "Patch the guest OS on EC2" → customer
- "Patch the RDS database OS" / "patch ELB" / "patch Lambda OS" → AWS
- "Secure the hypervisor" / "data center guards" / "dispose of disks" → AWS
- "Configure security groups" / "set password policy" / "configure IAM roles" → customer
- "Encrypt data client-side" → customer
- "Training employees" / "patching" / "configuration management" → shared
- "Classify data" / "who can access the S3 bucket or DynamoDB table" → customer
- "Proof of AWS's controls for auditors" → AWS Artifact

Details: [[2.1 Shared Responsibility Model]] · Cards: [[Flashcards - Domain 2]]
