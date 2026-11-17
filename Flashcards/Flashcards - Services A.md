---
tags:
  - flashcards/services
---
# Flashcards: Services A

Analytics, Application Integration, Business Productivity, Compute, Containers, Serverless, Database, Storage. Reference notes: [[Services - Analytics]], [[Services - Application Integration]], [[Services - Business Productivity]], [[Services - Compute]], [[Services - Containers]], [[Services - Serverless]], [[Services - Database]], [[Services - Storage]].

## Analytics

A team wants to run standard SQL queries directly against log files stored in S3 without loading them anywhere or managing servers. Which service?::Amazon Athena

How is Amazon Athena priced?::Per query, based on the amount of data scanned (serverless, no clusters)

A company wants to find and subscribe to third-party data sets (for example financial or weather data) and receive them in its AWS account. Which service?::AWS Data Exchange

AWS Data Exchange versus AWS Marketplace: which one is for third-party data sets rather than software?::AWS Data Exchange

A company wants to move its on-premises Apache Hadoop and Spark clusters to a managed AWS service. Which service?::Amazon EMR

A team needs a serverless ETL service that also crawls data sources and builds a central data catalog. Which service?::AWS Glue

Which AWS Glue component stores table definitions that Athena and Redshift Spectrum can use?::The AWS Glue Data Catalog

A company must ingest website clickstream data and analyze it in near real time. Which service family?::Amazon Kinesis

Which Kinesis capability loads streaming data into S3, Redshift, or OpenSearch with no code to manage?::Kinesis Data Firehose (now named Amazon Data Firehose)

Which Kinesis service ingests video from connected cameras for analytics and ML?::Kinesis Video Streams

A company runs Apache Kafka on premises and wants a fully managed Kafka service on AWS without code changes. Which service?::Amazon MSK (Amazon Managed Streaming for Apache Kafka)

Streaming question that mentions no specific open-source framework: Kinesis or MSK?::Kinesis (choose MSK only when Apache Kafka is named)

A company needs full-text search for its website and log analytics with dashboards, previously done with Elasticsearch. Which service?::Amazon OpenSearch Service

Amazon OpenSearch Service versus Amazon Kendra: which is ML-powered natural-language enterprise document search?::Amazon Kendra (OpenSearch is the search and log analytics engine)

Business users need interactive dashboards and visualizations built from data in S3, Athena, and Redshift. Which service?::Amazon QuickSight

What is SPICE in Amazon QuickSight?::Its in-memory calculation engine that makes dashboards fast

A company needs a petabyte-scale data warehouse for complex SQL analytics (OLAP) on historical structured data. Which service?::Amazon Redshift

Which Redshift feature queries data that stays in S3 without loading it into the warehouse?::Redshift Spectrum

Redshift or RDS for an application's transactional (OLTP) database?::RDS (Redshift is for analytics/OLAP)

## Application Integration

A company wants to react automatically to events from AWS services and SaaS applications by routing them to targets with rules. Which service?::Amazon EventBridge

Which service was formerly known as Amazon CloudWatch Events?::Amazon EventBridge

Administrators must receive an email or SMS alert when a CloudWatch alarm fires. Which service delivers it?::Amazon SNS

One message must be pushed simultaneously to several SQS queues and a Lambda function (fan-out). Which service?::Amazon SNS

SNS versus SQS: which is push-based pub/sub to many subscribers, and which is a pull-based queue?::SNS is push pub/sub; SQS is a pull-based queue

A web tier must hand orders to a processing tier so orders are not lost if the processor is slow or offline (decoupling). Which service?::Amazon SQS

Which SQS queue type guarantees order and exactly-once processing?::FIFO queue (Standard queues are at-least-once with best-effort ordering)

What is the default and maximum SQS message retention?::Default 4 days; maximum 14 days

A developer needs to coordinate several Lambda functions into a visual workflow with branching, retries, and waits. Which service?::AWS Step Functions

Step Functions versus EventBridge: which manages an ordered multi-step workflow with state?::AWS Step Functions (EventBridge routes individual events)

## Business Productivity

A company wants to set up a cloud-based customer call center with IVR and chat, without telephony hardware. Which service?::Amazon Connect

How does the reference guide describe Amazon Connect in three words?::Omnichannel cloud contact center

Amazon Connect versus Amazon Lex: which provides the full contact center, and which builds the chatbot?::Connect is the contact center; Lex builds the conversational bot that Connect can use

A company needs to send marketing campaigns and transactional emails (order confirmations) from its own domain. Which service?::Amazon SES (Simple Email Service)

SES versus SNS for email: which sends branded email to any address, and which sends plain notifications to confirmed topic subscribers?::SES sends branded email to any address; SNS email goes to confirmed subscribers only

## Compute

A research team must run hundreds of thousands of batch jobs and wants AWS to provision the right compute automatically. Which service?::AWS Batch

Does AWS Batch carry an additional service charge?::No; you pay only for the underlying compute (EC2, Spot, or Fargate)

A company needs virtual servers with full control of the operating system and the choice of instance type. Which service?::Amazon EC2

Which EC2 instance family fits batch processing, media transcoding, and high-performance web servers?::Compute optimized

Which EC2 instance family fits workloads needing high sequential read/write to large local data sets, such as data warehousing?::Storage optimized

Which EC2 instance family fits large in-memory data sets and in-memory databases?::Memory optimized

On EC2, who patches the guest operating system?::The customer

Developers want to upload their web application code and have AWS handle provisioning, load balancing, scaling, and monitoring. Which service?::AWS Elastic Beanstalk

What does AWS Elastic Beanstalk itself cost?::Nothing extra; you pay for the resources it creates (EC2, ELB, and so on)

Elastic Beanstalk versus CloudFormation: which takes application code, and which takes an infrastructure template?::Elastic Beanstalk takes application code; CloudFormation takes infrastructure-as-code templates

A small business with little AWS experience wants a simple WordPress site at a low, predictable monthly price. Which service?::Amazon Lightsail

Users in one large metropolitan area need single-digit millisecond latency to an application running on EC2. Which infrastructure option?::AWS Local Zones

A company must run AWS services inside its own data center for low latency to on-premises systems and local data residency. Which service?::AWS Outposts

Under AWS Outposts, who is responsible for the facility's power, networking, and physical security?::The customer (AWS installs and maintains the Outposts hardware)

An application must deliver ultra-low latency to mobile devices over 5G networks. Which service?::AWS Wavelength

Local Zones versus Wavelength: which is embedded in telecom 5G networks?::AWS Wavelength

A company must distribute incoming web traffic across EC2 instances in multiple Availability Zones and send it only to healthy instances. Which service?::Elastic Load Balancing

Which load balancer routes HTTP/HTTPS traffic by URL path at layer 7?::Application Load Balancer

Which load balancer handles TCP/UDP at layer 4 with ultra-high performance and static IP addresses?::Network Load Balancer

Which load balancer is used to deploy and scale third-party virtual appliances such as firewalls?::Gateway Load Balancer

An application's traffic varies unpredictably and the company wants EC2 capacity added and removed automatically. Which service?::Amazon EC2 Auto Scaling

Which cloud benefit does auto scaling provide, per task statement 3.3?::Elasticity

What three capacity settings define an Auto Scaling group?::Minimum, desired, and maximum capacity

EC2 Auto Scaling versus Elastic Load Balancing: which changes the number of instances?::EC2 Auto Scaling (ELB only spreads traffic across them)

## Containers

A company needs a private, managed registry to store Docker container images for ECS and EKS. Which service?::Amazon ECR (Elastic Container Registry)

ECR versus CodeArtifact: which stores container images, and which stores software packages such as npm or Maven libraries?::ECR stores container images; CodeArtifact stores software packages

A company wants to run Docker containers with AWS-native orchestration and no Kubernetes. Which service?::Amazon ECS

What are the two ways (launch types) to run ECS tasks?::EC2 launch type (you manage instances) or Fargate (serverless)

A company already runs Kubernetes on premises and wants a managed Kubernetes control plane on AWS. Which service?::Amazon EKS

ECS or EKS when the question mentions Kubernetes?::Amazon EKS

## Serverless

A company wants to run containers on ECS or EKS without provisioning or managing EC2 instances. Which service?::AWS Fargate

Is AWS Fargate a container orchestrator?::No; it is serverless compute that ECS or EKS run containers on

The reference guide lists Fargate under which category, while the exam guide lists it under Serverless?::Containers

A company wants code to run automatically whenever a file is uploaded to S3, with no servers and pay only when it runs. Which service?::AWS Lambda

What is the maximum run time of a single Lambda invocation?::15 minutes (900 seconds)

How is AWS Lambda billed?::Per request plus compute duration (based on memory allocated); nothing when idle

In the shared responsibility model, who patches the operating system used by Lambda?::AWS

## Database

A company wants a MySQL- and PostgreSQL-compatible relational database with higher performance and storage replicated across three AZs. Which service?::Amazon Aurora

Across how many Availability Zones does Aurora replicate its storage?::Three

Which Aurora option scales database capacity automatically for variable or unpredictable workloads?::Aurora Serverless

A gaming company needs a serverless NoSQL key-value database with single-digit millisecond latency at any scale. Which service?::Amazon DynamoDB

Which DynamoDB add-on provides microsecond read latency through in-memory caching?::DynamoDB Accelerator (DAX)

Which DynamoDB feature replicates tables across multiple Regions?::Global tables

A company needs an in-memory database that is durable enough to be its primary database, with Redis compatibility. Which service?::Amazon MemoryDB for Redis

MemoryDB versus ElastiCache: which is a durable primary database and which is mainly a cache?::MemoryDB is the durable primary database; ElastiCache is a cache

A social network needs to store and query highly connected relationships such as friends of friends. Which service?::Amazon Neptune

Which database fits fraud detection and recommendation engines built on relationships between entities?::Amazon Neptune (graph database)

A company needs a managed relational database running Oracle or Microsoft SQL Server without patching the OS. Which service?::Amazon RDS

RDS Multi-AZ versus read replicas: which provides high availability and which provides read scaling?::Multi-AZ provides high availability (synchronous standby, automatic failover); read replicas provide read scaling

On Amazon RDS, who patches the operating system and database software?::AWS

An application needs to reduce load on its RDS database by caching frequent query results in memory. Which service?::Amazon ElastiCache

Which open-source engines does ElastiCache support?::Redis OSS, Memcached, and Valkey

## Storage

A company wants one policy-based service to schedule and retain backups of EC2, EBS, RDS, DynamoDB, EFS, and S3 across accounts. Which service?::AWS Backup

Which AWS Backup feature makes backups immutable for compliance?::AWS Backup Vault Lock

An EC2 instance needs a persistent boot volume that survives stopping the instance. Which service?::Amazon EBS

An EBS volume is scoped to which part of the global infrastructure?::A single Availability Zone

Where are EBS snapshots stored, and are they full or incremental?::In Amazon S3; incremental

Which block storage option is fastest but loses its data when the instance stops or terminates?::EC2 instance store

Many Linux EC2 instances across several AZs need to share one NFS file system that grows automatically. Which service?::Amazon EFS

Can Windows EC2 instances use Amazon EFS?::No; use Amazon FSx for Windows File Server

A company needs disaster recovery for on-premises servers with RPOs of seconds and RTOs of minutes in AWS. Which service?::AWS Elastic Disaster Recovery

Elastic Disaster Recovery versus Application Migration Service: which is ongoing protection, and which is a one-time lift-and-shift?::Elastic Disaster Recovery is ongoing DR; Application Migration Service is a one-time migration

Windows applications need a managed shared file system using SMB with Active Directory integration. Which service?::Amazon FSx for Windows File Server

An HPC or machine learning workload needs a high-performance file system that can link to S3. Which service?::Amazon FSx for Lustre

A company needs virtually unlimited object storage for images, backups, and static website files. Which service?::Amazon S3

What durability is Amazon S3 designed for?::99.999999999% (11 nines)

Which S3 feature automatically moves objects to cheaper storage classes or deletes them after a set number of days?::S3 Lifecycle policies (lifecycle configuration)

Which S3 storage class is the lowest-cost storage in AWS, with retrieval within 12 hours?::S3 Glacier Deep Archive

What is the minimum storage duration for S3 Glacier Deep Archive?::180 days

What is the minimum storage duration for S3 Glacier Instant Retrieval and Flexible Retrieval?::90 days

Archived data is accessed about once a quarter but must be available in milliseconds. Which storage class?::S3 Glacier Instant Retrieval

What are the S3 Glacier Flexible Retrieval retrieval options?::Expedited 1 to 5 minutes; Standard 3 to 5 hours; Bulk 5 to 12 hours (free)

On-premises applications need low-latency local access to data stored in AWS through a cached file share. Which service?::AWS Storage Gateway

Which Storage Gateway type replaces physical tape backups with a virtual tape library in AWS?::Tape Gateway

Which Storage Gateway type presents NFS or SMB file shares on premises backed by objects in S3?::S3 File Gateway
