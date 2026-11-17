---
tags:
  - flashcards/domain-3
---
# Flashcards - Domain 3 (Part 2)

Task statements 3.5 to 3.8. Notes: [[3.5 Network Services]] · [[3.6 Storage Services]] · [[3.7 AI-ML and Analytics Services]] · [[3.8 Other In-Scope Service Categories]]

## 3.5 Network services

A subnet is placed in how many Availability Zones?::Exactly one

What makes a subnet public?::Its route table has a route to an internet gateway

Reference guide definition of an internet gateway?::A VPC component that allows communication between a user's computer and the internet

Reference guide definition of a NAT gateway?::A network address translation service that gives instances in a private subnet the ability to connect to services outside the VPC

Which gateway lets private-subnet instances download updates while blocking inbound connections from the internet?::NAT gateway

In which subnet type is a NAT gateway placed?::A public subnet

Which gateway sits on the AWS side of a Site-to-Site VPN connection?::Virtual private gateway

What is a customer gateway?::A physical or software appliance the customer owns and manages on premises (its end of the VPN)

Which gateway connects many VPCs, AWS accounts, and on-premises networks through one hub?::AWS Transit Gateway

Which gateway lets one Direct Connect connection reach VPCs in multiple Regions?::Direct Connect gateway

Is VPC peering transitive?::No. If A peers with B and B with C, A cannot reach C through B

What lets a VPC reach S3 or DynamoDB privately without an internet gateway or NAT gateway?::A VPC endpoint

Security group or network ACL - which operates at the instance level?::Security group

Security group or network ACL - which operates at the subnet level?::Network ACL

Which VPC firewall is stateful?::Security group (return traffic is automatically allowed)

Which VPC firewall is stateless?::Network ACL (return traffic needs its own rule)

Which VPC firewall supports explicit deny rules?::Network ACL (security groups have allow rules only)

How are network ACL rules evaluated?::In number order, lowest first; the first match applies

Default rules of a new security group?::Deny all inbound, allow all outbound

What are the three main functions of Route 53?::Domain registration; DNS routing; health checking

Which Route 53 routing policy splits traffic by percentages, for example 90/10?::Weighted routing

Which Route 53 routing policy sends users to the Region with the lowest latency?::Latency-based routing

Which Route 53 routing policy sends traffic to a standby when the primary fails a health check?::Failover routing

CloudFront vs Global Accelerator - which one caches content?::CloudFront (Global Accelerator does not cache)

Which edge service gives an application two static anycast IP addresses?::AWS Global Accelerator

Which edge service suits non-HTTP TCP or UDP traffic such as gaming or VoIP?::AWS Global Accelerator

Site-to-Site VPN traffic travels over which network?::The public internet, inside an encrypted IPsec tunnel

Which VPN type is for individual remote users' devices?::AWS Client VPN

Which connectivity option bypasses the public internet and gives consistent performance?::AWS Direct Connect

Is AWS Direct Connect traffic encrypted by default?::No. Run a VPN over it if encryption is required

Common highly available hybrid design using two connectivity options?::Direct Connect as primary with Site-to-Site VPN as backup

## 3.6 Storage services

Designed durability of every S3 storage class?::99.999999999% (11 nines)

Designed availability of S3 Standard?::99.99%

Designed availability of S3 Standard-IA?::99.9%

Designed availability of S3 One Zone-IA?::99.5%

How many AZs does S3 One Zone-IA use?::One (all other main classes use at least three)

Minimum storage duration for S3 Standard-IA and One Zone-IA?::30 days

Minimum storage duration for S3 Glacier Instant Retrieval and Glacier Flexible Retrieval?::90 days

Minimum storage duration for S3 Glacier Deep Archive?::180 days

Minimum storage duration for S3 Standard and S3 Intelligent-Tiering?::None

Which S3 class is cheapest for rarely accessed archive data that still needs millisecond retrieval?::S3 Glacier Instant Retrieval

Glacier Flexible Retrieval retrieval times for Expedited, Standard, and Bulk?::1 to 5 minutes; 3 to 5 hours; 5 to 12 hours

Glacier Deep Archive retrieval times for Standard and Bulk?::Within 12 hours; within 48 hours

Which S3 class suits unknown or changing access patterns?::S3 Intelligent-Tiering

What extra charge does S3 Intelligent-Tiering have, and what charge does it not have?::A small monthly monitoring and automation fee per object; no retrieval fees

What is the minimum billable object size for Standard-IA, One Zone-IA, and Glacier Instant Retrieval?::128 KB

Which S3 class fits infrequently accessed data that can easily be re-created, at the lowest IA price?::S3 One Zone-IA

What does the S3 Outposts storage class provide?::S3 buckets on AWS Outposts hardware on premises, for local data residency and processing

What two kinds of action can an S3 lifecycle rule take?::Transition objects to another storage class; expire (delete) objects

What S3 feature protects against accidental deletes and overwrites by keeping prior copies?::Versioning

What must be enabled on both buckets before S3 replication works?::Versioning

Which S3 feature gives write-once-read-many (WORM) protection?::S3 Object Lock

An EBS volume lives in how many Availability Zones?::One (replicated within that AZ)

Where are EBS snapshots stored, and are they full or incremental?::In Amazon S3 (managed by AWS); incremental

Which EBS volume family suits IOPS-heavy databases and boot volumes - SSD or HDD?::SSD (General Purpose or Provisioned IOPS)

Can an HDD-backed EBS volume (st1 or sc1) be a boot volume?::No

What happens to instance store data when the instance stops or terminates?::It is lost (it survives only a reboot)

Best use of EC2 instance store?::Temporary data such as caches, buffers, and scratch space

Shared NFS file system for many Linux instances across AZs?::Amazon EFS

Managed Windows file shares using SMB and Active Directory?::Amazon FSx for Windows File Server

FSx flavor for high-performance computing and ML training?::Amazon FSx for Lustre

Which Storage Gateway type presents NFS or SMB file shares that store data as S3 objects?::S3 File Gateway

Which Storage Gateway type presents iSCSI block volumes?::Volume Gateway

Volume Gateway cached mode vs stored mode?::Cached keeps primary data in AWS with hot data cached locally; stored keeps the full data set on premises with async backup to AWS

Which Storage Gateway type replaces a physical tape library for existing backup software?::Tape Gateway

Which service centrally manages backup plans and retention across many AWS services and on-premises VMware?::AWS Backup

Which service continuously replicates servers so they can be recovered in AWS within minutes?::AWS Elastic Disaster Recovery

When does the exam expect an AWS Snow Family device?::Large data volumes with limited bandwidth, or edge computing at sites with little or no connectivity

## 3.7 AI/ML and analytics services

Which AWS ML service is for building, training, and deploying your own custom models, rather than calling a pre-trained API?::Amazon SageMaker

Transcribe vs Polly - which direction does each convert?::Transcribe converts speech to text; Polly converts text to speech

Comprehend vs Textract?::Comprehend finds meaning in text (sentiment, entities); Textract extracts text and form fields from scanned documents

Rekognition vs Textract?::Rekognition analyzes images and video (faces, objects, scenes); Textract reads documents and forms keeping table structure

Lex vs Kendra?::Lex builds conversational chatbots; Kendra searches company documents to answer questions

Which AI services chain together to turn foreign-language call recordings into English sentiment scores?::Transcribe (speech to text), Translate (to English), Comprehend (sentiment)

Which two services together create a voice chatbot that understands and speaks?::Amazon Lex and Amazon Polly

Athena vs Redshift - which needs data loaded into it first?::Redshift (Athena queries data in place in S3)

Athena vs EMR?::Athena runs serverless SQL directly on S3; EMR runs managed Hadoop and Spark clusters

Which AWS Glue component do Athena and Redshift Spectrum use for table definitions?::The AWS Glue Data Catalog

Kinesis vs SQS?::Kinesis is real-time streaming that many consumers can read and analyze; SQS is a message queue for decoupling

When is Amazon MSK the answer instead of Kinesis?::When the scenario names Apache Kafka

Place these on the analytics pipeline in order - QuickSight, Kinesis, Athena, Glue.::Kinesis (ingest); Glue (catalog and ETL); Athena (query); QuickSight (visualize)

## 3.8 Other in-scope service categories

SNS vs SQS - which is push publish/subscribe and which is a pull queue?::SNS is push pub/sub; SQS is a pull queue

Which service sends one alert to many subscribers such as email, SMS, Lambda, and SQS?::Amazon SNS

Which service decouples components by buffering messages until consumers process them?::Amazon SQS

SQS queue type that guarantees order and exactly-once processing?::FIFO queue

EventBridge vs SNS?::EventBridge routes events by content rules from AWS, SaaS, and schedules; SNS pushes messages to topic subscribers

Step Functions vs SQS?::Step Functions orchestrates an ordered multi-step workflow; SQS only holds messages

What is the SNS fan-out pattern?::An SNS topic delivers each message to several SQS queues for independent processing

SES vs SNS for sending email?::SES for customized high-volume application or marketing email; SNS for simple notifications to topic subscribers

AMS vs AWS IQ vs AWS Support?::AMS has AWS operate your infrastructure; AWS IQ connects you with freelance AWS Certified experts; AWS Support answers technical cases under a plan

Order the core Code services in a CI/CD flow.::CodeCommit (source); CodeBuild (build and test); CodeDeploy (deploy); all orchestrated by CodePipeline

CodeBuild vs CodeDeploy?::CodeBuild compiles and tests code into artifacts; CodeDeploy installs releases on EC2, on-premises servers, Lambda, or ECS

X-Ray vs CloudWatch?::X-Ray traces individual requests through an application; CloudWatch collects metrics, logs, and alarms

Cloud9 vs CloudShell?::Cloud9 is a browser-based IDE for writing code; CloudShell is a pre-authenticated browser shell for CLI commands

WorkSpaces vs AppStream 2.0 vs WorkSpaces Web?::WorkSpaces streams a full desktop; AppStream 2.0 streams single applications; WorkSpaces Web gives a secure browser for internal sites and SaaS

Which end-user computing services present the output of VMs on end-user machines?::Amazon WorkSpaces and Amazon AppStream 2.0

Amplify vs AppSync?::Amplify builds and hosts full-stack web and mobile apps; AppSync provides managed GraphQL APIs

IoT Core vs IoT Greengrass - where does each run?::IoT Core runs in the AWS Cloud; Greengrass runs on devices at the edge

Which IoT service lets devices process data locally and keep working offline?::AWS IoT Greengrass
