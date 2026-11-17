---
tags:
  - clf-c02
  - cheat-sheet
---
# Database Picker

## Pick the database

| Cue in the question | Answer | Model |
| --- | --- | --- |
| Relational, SQL, Oracle / SQL Server / MySQL / PostgreSQL / MariaDB, less admin | Amazon RDS | Relational (OLTP) |
| MySQL/PostgreSQL compatible, higher performance, 6 copies in 3 AZs, up to 15 replicas | Amazon Aurora | Relational (OLTP) |
| NoSQL, key-value, serverless, single-digit ms at any scale, schemaless | Amazon DynamoDB | Key-value / document |
| Microsecond reads for DynamoDB | DAX | In-memory cache |
| Cache in front of a database, session store | Amazon ElastiCache | In-memory cache |
| Durable in-memory primary database, Redis compatible | Amazon MemoryDB for Redis | In-memory database |
| Relationships: social network, fraud detection, recommendations | Amazon Neptune | Graph |
| Data warehouse, petabyte analytics, BI, OLAP | Amazon Redshift | Columnar warehouse |
| Need OS access or unsupported engine/version | Database on EC2 | Self-managed |

Distractors only (not in scope): DocumentDB = MongoDB · Keyspaces = Cassandra · Timestream = time series · QLDB = ledger (shut down July 31, 2025).

## RDS features

| Feature | Purpose | How |
| --- | --- | --- |
| Multi-AZ | High availability | Synchronous standby in another AZ, automatic failover |
| Read replicas | Read scaling | Asynchronous read-only copies, can be cross-Region |
| Automated backups | Point-in-time recovery | Retention up to 35 days |
| Manual snapshots | Keep until deleted | User-initiated |

Mnemonic: **Multi-AZ = Availability; Replicas = Reads.**

## EC2-hosted vs managed

| Task | EC2 | RDS |
| --- | --- | --- |
| OS and DB patching, backups, HA | Customer | AWS |
| Data, access, network rules, query tuning | Customer | Customer |

## Migration

| Scenario | Tools |
| --- | --- |
| Same engine (homogeneous), e.g., MySQL → Aurora MySQL | DMS |
| Different engine (heterogeneous), e.g., Oracle → Aurora PostgreSQL | SCT (convert schema) then DMS (move data) |
| Minimal downtime, source stays online, continuous replication | DMS |
| Huge database, limited bandwidth | Snow Family device, then DMS |

DMS **moves data**; SCT **converts schema**.

Links: [[3.4 Database Services]] · [[Services - Database]] · [[Services - Migration and Transfer]] · [[Services - Analytics#Amazon Redshift|Amazon Redshift]] · [[Commonly Confused Services]]
