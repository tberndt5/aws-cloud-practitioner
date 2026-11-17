---
tags:
  - clf-c02
  - services
  - services/database
category: "Database"
status: not-started
---
# Services: Database

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Concepts (relational versus NoSQL, EC2-hosted versus AWS managed databases, in-memory databases, database migration) are taught in [[3.4 Database Services]]. Amazon ElastiCache is included here because task statement 3.4 asks you to identify memory-based databases.

Cross-listings: the reference guide lists **Amazon Redshift** under Database, but the exam guide lists it under Analytics; see [[Services - Analytics#Amazon Redshift|Amazon Redshift]]. Database migration tools are in Migration and Transfer: [[Services - Migration and Transfer#AWS Database Migration Service (AWS DMS)|AWS DMS]] and [[Services - Migration and Transfer#AWS Schema Conversion Tool (AWS SCT)|AWS SCT]].

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#Amazon Aurora\|Amazon Aurora]] | AWS-built high-performance MySQL/PostgreSQL-compatible relational database | "MySQL or PostgreSQL compatible", "high performance and availability", "commercial-grade at open-source cost" |
| [[#Amazon DynamoDB\|Amazon DynamoDB]] | Serverless NoSQL key-value and document database | "NoSQL", "key-value", "single-digit millisecond at any scale", "schemaless" |
| [[#Amazon MemoryDB for Redis\|Amazon MemoryDB for Redis]] | Durable in-memory primary database, Redis-compatible | "in-memory database that is durable", "primary database with microsecond reads" |
| [[#Amazon Neptune\|Amazon Neptune]] | Managed graph database | "graph", "highly connected data", "social network", "fraud detection", "recommendations" |
| [[#Amazon RDS\|Amazon RDS]] | Managed relational database with common commercial and open-source engines | "relational", "SQL", "Oracle/SQL Server/MySQL", "managed database, no OS patching" |
| [[#Amazon ElastiCache\|Amazon ElastiCache]] | Managed in-memory cache (Redis/Memcached) | "cache", "reduce database load", "session store", "microsecond latency" |

> [!tip] EC2-hosted or managed?
> Run the database **on EC2** only when you need OS-level access or an engine/version/configuration a managed service does not offer; you then patch the OS and database and handle backups and HA yourself. Otherwise choose a **managed** service (RDS, Aurora, DynamoDB), where AWS handles patching, backups, and failover.

## Amazon Aurora

> [!summary] Database engine that is compatible with MySQL and PostgreSQL.

- **What it does:** Aurora is a fully managed relational database built by AWS for the cloud and offered as part of Amazon RDS. It is compatible with MySQL and PostgreSQL, so existing code and tools work, but it uses a distributed, self-healing storage layer that gives higher performance and availability than standard engines.
- **Choose it when:** the question says "MySQL- or PostgreSQL-compatible with higher performance", "commercial-grade database at open-source cost", "highly available relational database", or "relational database that scales storage automatically".
- **Key facts:**
  - ==Storage is automatically replicated across three Availability Zones== in a Region, and grows automatically as data grows.
  - Up to 15 low-latency read replicas; continuous backup to S3 with point-in-time recovery.
  - Marketed as several times the throughput of standard MySQL and PostgreSQL (exam-era materials say up to 5x MySQL and 3x PostgreSQL; the current product page says 6x).
  - **Aurora Serverless** scales capacity automatically for variable workloads; **Aurora Global Database** spans multiple Regions.
  - Named in task statement 3.4 as a relational database example.
- **Don't confuse with:** **RDS for MySQL/PostgreSQL** (standard community engines on RDS; Aurora is AWS's own higher-performance engine). **Redshift** (analytics data warehouse, not transactional). **DynamoDB** (NoSQL).
- **Docs:** [What is Amazon Aurora?](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html)

## Amazon DynamoDB

> [!summary] NoSQL database service with fast and predictable performance and seamless scalability; schemaless.

- **What it does:** DynamoDB is a fully managed, serverless NoSQL database that stores data as key-value pairs and documents. There are no servers or database software to manage; tables scale automatically to handle very large request volumes with consistent single-digit millisecond response times.
- **Choose it when:** the question says "NoSQL", "key-value", "schemaless/flexible schema", "serverless database", "massive scale with low latency", or workloads like gaming leaderboards, shopping carts, session data, or IoT data.
- **Key facts:**
  - ==Serverless NoSQL with single-digit millisecond performance at any scale==.
  - Data automatically replicated across multiple AZs in a Region; **global tables** replicate across Regions (multi-Region, multi-active).
  - Capacity modes: on-demand (pay per request) or provisioned (set read/write capacity, optionally auto scaled).
  - **DynamoDB Accelerator (DAX)** is an in-memory cache that brings reads to microseconds.
  - Shared responsibility: the customer still decides which users and services have access to tables (IAM), per the reference guide.
  - Named in task statements 1.4 (managed service) and 3.4 (NoSQL example).
- **Don't confuse with:** **RDS/Aurora** (relational, SQL, fixed schema, joins). **ElastiCache/MemoryDB** (in-memory). **DocumentDB** (MongoDB-compatible document database; not in scope). **Neptune** (graph relationships).
- **Docs:** [What is Amazon DynamoDB?](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)

## Amazon MemoryDB for Redis

> [!summary] Durable, in-memory database service that delivers ultra-fast performance.

- **What it does:** MemoryDB is a Redis-compatible database that keeps the entire data set in memory for microsecond reads, while also writing every change to a durable transaction log stored across multiple Availability Zones. That durability means it can be the **primary** database for an application, not just a cache.
- **Choose it when:** the question asks for an "in-memory database" that is also "durable", a "primary database with ultra-fast performance", or Redis compatibility without a separate backing database.
- **Key facts:**
  - ==In-memory and durable (Multi-AZ transaction log)== — the difference from a cache.
  - Microsecond read latency and single-digit millisecond write latency.
  - Compatible with Redis APIs and data structures.
  - Current status: MemoryDB now also offers a Valkey engine (an open-source fork of Redis), and AWS pages now call the service Amazon MemoryDB.
- **Don't confuse with:** **ElastiCache** (a cache in front of another database; data can be lost and rebuilt). **DynamoDB + DAX** (NoSQL database with a cache add-on). **RDS** (disk-based relational).
- **Docs:** [What is Amazon MemoryDB?](https://docs.aws.amazon.com/memorydb/latest/devguide/what-is-memorydb.html)

## Amazon Neptune

> [!summary] Graph database service for highly connected datasets.

- **What it does:** Neptune is a fully managed graph database. A graph database stores entities (nodes) and the relationships between them (edges), so questions like "friends of friends who bought this product" run quickly even across billions of relationships.
- **Choose it when:** the question mentions "relationships between data", "highly connected data", "social networking", "recommendation engines", "fraud detection", "knowledge graphs", or "network/IT topology".
- **Key facts:**
  - Purpose-built graph database; supports the popular graph query languages (Apache TinkerPop Gremlin, openCypher, SPARQL for RDF).
  - Highly available, with storage replicated across multiple AZs and up to 15 read replicas.
  - Keyword to match: ==graph = Neptune==.
- **Don't confuse with:** **DynamoDB** (key-value lookups, not relationship traversal). **RDS** (relational tables; joins across many levels get slow). **Amazon Kendra/OpenSearch** (search, not graph).
- **Docs:** [What is Amazon Neptune?](https://docs.aws.amazon.com/neptune/latest/userguide/intro.html)

## Amazon RDS

> [!summary] Set up, operate, and scale a relational database in the cloud.

- **What it does:** Amazon Relational Database Service (RDS) runs familiar relational database engines as a managed service. AWS handles hardware provisioning, OS and database software installation and patching, automated backups, failure detection, and recovery; you manage the data, schema, queries, and access.
- **Choose it when:** the question needs a relational (SQL) database for an application (OLTP, online transaction processing), a specific commercial engine such as Oracle or SQL Server, or "a managed database so we don't patch the OS".
- **Key facts:**
  - Engines: Amazon Aurora, MySQL, PostgreSQL, MariaDB, Oracle, Microsoft SQL Server. Current status: IBM Db2 has since been added as an RDS engine, after the exam materials were written.
  - ==**Multi-AZ** deployment = high availability (a synchronous standby in another AZ with automatic failover); **read replicas** = read scaling (asynchronous copies that serve reads)==.
  - Automated backups with point-in-time recovery, plus manual snapshots.
  - Shared responsibility: ==AWS patches the OS and database software of RDS instances==; the customer manages database users, security groups, encryption choices, and query tuning (see [[2.1 Shared Responsibility Model]]).
  - Supports Reserved Instances for discounts on steady workloads; BYOL is available for some Oracle editions.
- **Don't confuse with:** **Aurora** (AWS-built engine inside the RDS family with higher performance and auto-growing storage). **Database on EC2** (you patch the OS and DB). **Redshift** (analytics/OLAP). **DynamoDB** (NoSQL).
- **Docs:** [What is Amazon RDS?](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)

## Amazon ElastiCache

> [!summary] Fully managed in-memory caching service that improves application performance by retrieving data from fast in-memory stores instead of slower disk-based databases. (Not in the reference guide; summary written for this vault.)

- **What it does:** ElastiCache runs managed in-memory data stores compatible with Redis and Memcached. Applications put frequently read data (query results, session state, leaderboards) in the cache so repeated reads return in microseconds and the main database does less work.
- **Choose it when:** the question says "cache", "improve read performance of a database", "reduce load on RDS", "store session state", "microsecond latency", or "in-memory data store".
- **Key facts:**
  - Engines: Redis (Redis OSS), Memcached, and Valkey.
  - Sits in front of a database (RDS, Aurora, DynamoDB) to speed up reads; data is typically also kept in that backing database.
  - Fully managed: AWS handles setup, patching, monitoring, and failure recovery; a serverless option is available.
  - Answers the 3.4 skill "identifying memory-based databases" together with MemoryDB.
- **Don't confuse with:** **MemoryDB** (durable primary in-memory database; ElastiCache is primarily a cache). **DAX** (cache built only for DynamoDB). **CloudFront** (caches web content at edge locations, not database queries).
- **Docs:** [What is Amazon ElastiCache?](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
