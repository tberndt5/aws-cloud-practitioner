---
tags:
  - flashcards/domain-3
---
# Flashcards - Domain 3 (Part 1)

Task statements 3.1 to 3.4. Notes: [[3.1 Deploying and Operating in the AWS Cloud]] · [[3.2 AWS Global Infrastructure]] · [[3.3 Compute Services]] · [[3.4 Database Services]]

## 3.1 Deploying and operating in the AWS Cloud

What do the Management Console, CLI, SDKs, and CloudFormation all ultimately call::The AWS service APIs

Which access method is best for a one-time task done visually in a browser::AWS Management Console

Which access method runs AWS commands from a terminal or shell script::AWS CLI

Which access method lets developers call AWS services from application code in their programming language::AWS SDKs

What is AWS CloudShell::A browser-based, pre-authenticated shell launched from the console, with the AWS CLI preinstalled

How much persistent storage does CloudShell provide::Up to 1 GB per Region in your home directory, at no extra charge

What does infrastructure as code (IaC) mean::Defining infrastructure in text templates so a service provisions it automatically and repeatably

Which AWS service provides infrastructure as code with templates::AWS CloudFormation

What is a CloudFormation stack::The set of resources created and managed together from one template

Requirement says repeatable, consistent environments across accounts or Regions. Best approach::Infrastructure as code with AWS CloudFormation

Requirement says a quick one-time check of a setting. Best approach::AWS Management Console

Elastic Beanstalk vs CloudFormation in one line each::Beanstalk deploys your application code on managed infrastructure (PaaS); CloudFormation provisions any infrastructure from a template (IaC)

Which cloud service model gives the most control over the operating system::IaaS (for example, Amazon EC2)

Which cloud service model removes infrastructure management so you only deploy your application::PaaS (for example, AWS Elastic Beanstalk)

Which cloud service model is complete software run and managed by the vendor::SaaS

Name the three deployment models in the exam guide::Cloud, hybrid, on-premises

What is a hybrid deployment::Cloud resources connected to infrastructure and applications that stay on premises

What does AWS also call the on-premises deployment model::Private cloud

What does AWS Outposts provide::AWS infrastructure, services, APIs, and tools on customer premises

What is AWS Site-to-Site VPN::Encrypted IPsec tunnels over the internet between an on-premises network and a VPC

Site-to-Site VPN vs Client VPN::Site-to-Site connects whole networks; Client VPN connects individual users' devices

What is AWS Direct Connect::A private dedicated network connection from an on-premises data center to AWS that does not use the public internet

Direct Connect vs VPN on setup time::VPN in minutes; Direct Connect takes weeks

Is Direct Connect traffic encrypted by default::No; add a VPN over it (or MACsec) if encryption is required

Common backup for a Direct Connect link::A Site-to-Site VPN over the internet

## 3.2 AWS global infrastructure

Reference guide definition of a Region::Isolated geographic area that consists of multiple Availability Zones

Reference guide definition of an Availability Zone::One or more data centers within a Region

Reference guide definition of edge locations::A worldwide network of data centers that optimizes latency and throughput to users

Minimum number of AZs in an AWS Region::Three

Maximum distance between AZs in a Region::Within 100 km (60 miles) of each other

Why do AZs not share single points of failure::Each is physically separate with redundant, independent power, cooling, and networking

How do you achieve high availability within a Region::Deploy across multiple AZs (for example, ELB plus Auto Scaling across AZs, RDS Multi-AZ)

Is a single very large EC2 instance highly available::No; it is a single point of failure in one AZ

Four reasons to use multiple Regions::Disaster recovery, business continuity, low latency for global users, data sovereignty

Four factors for choosing a Region::Compliance and data sovereignty, latency to users, service availability, pricing

Which Region-selection factor usually decides first when laws apply::Compliance and data sovereignty

Can you launch EC2 instances in an edge location::No; edge locations serve CloudFront, Global Accelerator, Route 53, and edge security

What are AWS Local Zones::Extensions of a Region that place AWS resources close to large population and industry centers

What is AWS Wavelength::AWS compute and storage embedded in telecom 5G networks for ultra-low latency to mobile devices

Low latency for users in one specific city, AWS-run site. Which option::AWS Local Zones

Ultra-low latency to mobile devices over 5G. Which option::AWS Wavelength (Wavelength Zones)

Local Zones vs Wavelength vs Outposts by location::Metro area (Local Zones); telecom 5G network (Wavelength); customer data center (Outposts)

CloudFront vs Global Accelerator on caching::CloudFront caches content; Global Accelerator does not cache

What does Global Accelerator give you::Static anycast IP addresses and routing over the AWS global network to healthy endpoints

Edge service for TCP/UDP gaming or VoIP needing static IPs::AWS Global Accelerator

High availability vs disaster recovery scope::Multi-AZ protects against data center or AZ failure; multi-Region protects against Region-wide failure

## 3.3 Compute services

What is an AMI::Amazon Machine Image, the template of OS, software, and configuration used to launch EC2 instances

Who patches the guest OS on EC2::The customer

Instance family for balanced web servers and code repositories::General purpose

Instance family for batch processing, media transcoding, and dedicated game servers::Compute optimized

Instance family for in-memory databases and real-time big data analytics::Memory optimized

Instance family for high sequential read/write to large local data sets (NoSQL, data warehousing)::Storage optimized

Instance family for ML training and graphics with GPUs::Accelerated computing

ECS vs EKS::ECS is AWS-native container orchestration; EKS is managed Kubernetes

ECR vs ECS::ECR stores container images; ECS runs containers

What is AWS Fargate::Serverless compute engine for containers that works with ECS and EKS, so no EC2 instances to manage

Maximum duration of one Lambda invocation::15 minutes

Lambda vs Fargate in one line::Lambda runs event-triggered functions up to 15 minutes; Fargate runs containers with no time limit

Four traits of serverless::No servers to manage, automatic scaling, built-in availability, pay for use

Which compute option suits long-running containerized microservices without server management::AWS Fargate

Which service offers simple servers with a predictable monthly price for small websites::Amazon Lightsail

Which service schedules and runs large numbers of batch jobs and provisions the compute::AWS Batch

What does Auto Scaling provide in cloud-benefit terms::Elasticity (capacity matches demand automatically)

Three size settings of an EC2 Auto Scaling group::Minimum, desired, maximum

EC2 Auto Scaling vs AWS Auto Scaling::EC2 Auto Scaling scales EC2 groups; AWS Auto Scaling scales multiple services (EC2, ECS, DynamoDB, Aurora) from scaling plans

Horizontal vs vertical scaling::Horizontal adds or removes instances (scale out/in); vertical changes instance size (scale up/down)

Purpose of Elastic Load Balancing::Distribute incoming traffic across healthy targets in one or more AZs

Load balancer for HTTP/HTTPS with path-based routing::Application Load Balancer (layer 7)

Load balancer for TCP/UDP with extreme performance and static IPs::Network Load Balancer (layer 4)

Load balancer for third-party firewall and intrusion prevention appliances::Gateway Load Balancer

Auto Scaling vs load balancer in one line::Auto Scaling sets how many instances run; the load balancer decides which instance gets each request

## 3.4 Database services

Main reason to choose a managed database over a database on EC2::AWS handles patching, backups, high availability, and scaling, reducing operational overhead

When is a database on EC2 the better choice::When you need OS access or an engine, version, or configuration the managed service doesn't support

Name the RDS database engines in the exam era::Aurora, MySQL, PostgreSQL, MariaDB, Oracle, Microsoft SQL Server

Purpose of RDS Multi-AZ::High availability with a synchronous standby in another AZ and automatic failover

Purpose of RDS read replicas::Scale read traffic with asynchronous read-only copies

Multi-AZ vs read replicas mnemonic::Multi-AZ equals Availability; Replicas equal Reads

Maximum retention for RDS automated backups::35 days

Which engines is Aurora compatible with::MySQL and PostgreSQL

How does Aurora store data for durability::Six copies across three AZs

Maximum Aurora read replicas::15

Relational database needed for Oracle. RDS or Aurora::RDS (Aurora supports only MySQL- and PostgreSQL-compatible editions)

OLTP vs OLAP::OLTP handles many small transactions (RDS, Aurora, DynamoDB); OLAP runs large analytical queries (Redshift)

DynamoDB data models::Key-value and document

DynamoDB performance claim::Single-digit millisecond performance at any scale

What DynamoDB feature replicates tables across Regions::Global tables

What is DAX::DynamoDB Accelerator, an in-memory cache that gives DynamoDB microsecond read latency

ElastiCache vs MemoryDB::ElastiCache is an in-memory cache; MemoryDB is a durable in-memory primary database

Database type for social networks, fraud detection, and recommendation engines::Graph (Amazon Neptune)

Out-of-scope distractor for MongoDB workloads::Amazon DocumentDB

DMS vs SCT::DMS migrates the data; SCT converts the schema between engines

What happens to the source database during a DMS migration::It stays fully operational, minimizing downtime

Homogeneous migration::Same engine at source and target; DMS alone

Heterogeneous migration::Different engines; SCT converts the schema first, then DMS moves the data

Tools to migrate Oracle to Aurora PostgreSQL::AWS SCT, then AWS DMS

DMS vs Application Migration Service::DMS migrates databases; Application Migration Service rehosts whole servers
