---
tags:
  - flashcards/confused
---
# Flashcards - Commonly Confused

Each card pits look-alike services against each other. Reference: [[Commonly Confused Services]].

## Monitoring, auditing, configuration

CloudTrail vs CloudWatch: which one tells you which IAM user terminated an instance?::CloudTrail (records API calls and who made them)

CloudTrail vs Config: which one shows what a security group's rules looked like last Tuesday?::AWS Config (configuration history)

CloudWatch vs CloudTrail: which one raises an alarm when CPU utilization stays above 80%?::Amazon CloudWatch

CloudWatch vs X-Ray: which one traces a single request across microservices to find the slow component?::AWS X-Ray

## Threat detection and security findings

GuardDuty vs Inspector: which one finds unpatched software vulnerabilities (CVEs) on EC2 instances?::Amazon Inspector

GuardDuty vs Inspector: which one alerts that an instance is communicating with a known crypto-mining IP?::Amazon GuardDuty

Macie vs GuardDuty: which one discovers credit card numbers stored in S3 objects?::Amazon Macie

GuardDuty vs Detective: which one helps investigate the root cause after a finding is raised?::Amazon Detective

Security Hub vs GuardDuty: which one aggregates and prioritizes findings from GuardDuty, Inspector, and Macie across accounts?::AWS Security Hub

## Network protection

Shield vs WAF: which one blocks SQL injection and cross-site scripting requests?::AWS WAF

Shield Standard vs Shield Advanced: which one adds a 24/7 response team and DDoS cost protection?::Shield Advanced

WAF vs Firewall Manager: which one centrally applies WAF rules to every account in an organization?::AWS Firewall Manager

WAF vs Network Firewall: which one provides stateful intrusion prevention for all traffic entering a VPC?::AWS Network Firewall

Security group vs network ACL: which one is stateless?::Network ACL

Security group vs network ACL: which one can contain explicit deny rules?::Network ACL (security groups only allow)

## Keys, certificates, secrets

KMS vs CloudHSM: which gives you a dedicated single-tenant HSM where only you control the keys?::AWS CloudHSM

KMS vs ACM: which one issues and auto-renews the TLS certificate for an HTTPS load balancer?::AWS Certificate Manager (ACM)

Secrets Manager vs Parameter Store: which one has built-in automatic rotation of database credentials?::AWS Secrets Manager

## Identity

IAM Identity Center vs Cognito: employees need one sign-in to 40 AWS accounts. Which?::IAM Identity Center (AWS Single Sign-On)

IAM Identity Center vs Cognito: a mobile app's customers sign in with Google or Facebook. Which?::Amazon Cognito

Directory Service vs IAM Identity Center: which one runs managed Microsoft Active Directory in AWS?::AWS Directory Service

## Compliance

Artifact vs Audit Manager: an auditor wants AWS's own SOC 2 report. Which?::AWS Artifact

Artifact vs Audit Manager: you need to continuously collect evidence of your own AWS usage for a PCI audit. Which?::AWS Audit Manager

## Recommendations and health

Trusted Advisor vs Compute Optimizer: which one uses ML on utilization metrics to recommend a smaller EC2 instance type?::AWS Compute Optimizer

Trusted Advisor vs Well-Architected Tool: which one reviews a specific workload by answering questions about the six pillars?::AWS Well-Architected Tool

Trusted Advisor vs Health Dashboard: which one warns that AWS will retire the host under your instance next week?::AWS Health Dashboard

Inspector vs Trusted Advisor: which one checks whether the root user has MFA and whether access keys are exposed?::AWS Trusted Advisor

## Billing tools

Budgets vs Cost Explorer: which one emails you when forecasted spend will exceed $1,000 this month?::AWS Budgets

Cost Explorer vs Cost and Usage Report: which one is the most detailed line-item data, delivered to S3?::AWS Cost and Usage Report (CUR)

Pricing Calculator vs Cost Explorer: which one estimates the cost of an architecture you have not built yet?::AWS Pricing Calculator

Billing Conductor vs Cost Explorer: which one produces pro forma bills with custom rates for showback and chargeback?::AWS Billing Conductor

## Multi-account governance

Organizations vs Control Tower: which one sets up a governed landing zone with guardrails in a few clicks?::AWS Control Tower

Service Catalog vs Control Tower: users must self-provision only IT-approved products. Which?::AWS Service Catalog

## Pricing models

Dedicated Hosts vs Dedicated Instances: which one gives socket and core visibility for server-bound BYOL licenses?::Dedicated Hosts

Reserved Instances vs Savings Plans: which commits to a dollar-per-hour spend rather than an instance configuration?::Savings Plans

Compute Savings Plans vs EC2 Instance Savings Plans: which one also covers Fargate and Lambda?::Compute Savings Plans

Capacity Reservation vs Reserved Instance: which reserves capacity in an AZ with no term commitment?::On-Demand Capacity Reservation

## Application integration

SNS vs SQS: which one pushes a single message to many subscribers at once?::Amazon SNS

SNS vs SQS: which one holds messages until a consumer pulls them, so a slow back end does not lose orders?::Amazon SQS

EventBridge vs SNS: which one routes events from SaaS partners and AWS services using rules and schedules?::Amazon EventBridge

## Networking

CloudFront vs Global Accelerator: a UDP game needs two static IP addresses worldwide. Which?::AWS Global Accelerator

Direct Connect vs Site-to-Site VPN: which one does not traverse the public internet?::AWS Direct Connect

Direct Connect vs Site-to-Site VPN: which one is encrypted by default and can be set up in hours?::AWS Site-to-Site VPN

Site-to-Site VPN vs Client VPN: remote employees connect laptops to the VPC. Which?::AWS Client VPN

Amazon Connect vs AWS Direct Connect: which one is a cloud contact center?::Amazon Connect

Internet gateway vs NAT gateway: private-subnet instances need outbound-only internet access. Which?::NAT gateway

## Global infrastructure

Local Zones vs Wavelength: which one is inside a telecom provider's 5G network?::AWS Wavelength

Local Zones vs Outposts: which one runs AWS racks in your own data center?::AWS Outposts

## Compute and containers

ECS vs EKS: the team already runs Kubernetes on premises and wants the same tooling. Which?::Amazon EKS

Lambda vs Fargate: a containerized job runs for three hours. Which can run it serverlessly?::AWS Fargate (Lambda stops at 15 minutes)

Elastic Beanstalk vs CloudFormation: developers want to upload code and have AWS handle capacity, load balancing, and scaling. Which?::AWS Elastic Beanstalk

## Developer tools

CodeBuild vs CodeDeploy: which one compiles source and runs unit tests?::AWS CodeBuild

Cloud9 vs CloudShell: which one is a pre-authenticated browser shell for running CLI commands?::AWS CloudShell

## Storage

EBS vs instance store: which one keeps data after the instance is stopped?::Amazon EBS

EFS vs FSx: Windows servers need an SMB file share joined to Active Directory. Which?::Amazon FSx for Windows File Server

S3 vs Storage Gateway: on-premises applications need local cached access to data stored in AWS. Which?::AWS Storage Gateway

## Databases

RDS vs Aurora: which one is AWS-built, MySQL and PostgreSQL compatible, and keeps six copies across three AZs?::Amazon Aurora

ElastiCache vs MemoryDB: which one is a durable in-memory primary database?::Amazon MemoryDB for Redis

Neptune vs DynamoDB: a fraud team needs to query relationships between accounts, devices, and cards. Which?::Amazon Neptune

## Analytics

Athena vs Redshift: which one runs SQL directly on files in S3 with no cluster to load?::Amazon Athena

## Migration

DMS vs SCT: which one converts an Oracle schema and stored procedures to PostgreSQL?::AWS SCT

Application Migration Service vs Application Discovery Service: which one replicates servers to EC2 for lift-and-shift?::AWS Application Migration Service

DataSync vs Snow Family: 500 TB must move but the site has a slow internet link. Which?::AWS Snow Family

## Machine learning

Polly vs Transcribe: which one converts speech to text?::Amazon Transcribe

Comprehend vs Kendra: which one detects sentiment in product reviews?::Amazon Comprehend

Kendra vs Lex: employees ask natural-language questions answered from internal documents. Which?::Amazon Kendra

Textract vs Rekognition: which one extracts form fields and tables from scanned invoices?::Amazon Textract

## End-user computing, frontend, IoT

WorkSpaces vs AppStream 2.0: users need only one desktop application streamed to a browser. Which?::Amazon AppStream 2.0

WorkSpaces Web vs WorkSpaces: staff need secure browser access to internal websites and SaaS apps only. Which?::Amazon WorkSpaces Web

Amplify vs AppSync: which one is a managed GraphQL API service?::AWS AppSync

IoT Core vs IoT Greengrass: devices must process data locally while offline. Which?::AWS IoT Greengrass

## Help and support

Professional Services vs AWS IQ: which one hires an AWS Certified freelancer for a short project?::AWS IQ

AWS Managed Services vs Professional Services: which one operates your infrastructure day to day?::AWS Managed Services (AMS)

AWS Support vs Trust and Safety: an AWS IP address is sending spam to your servers. Whom do you contact?::AWS Trust and Safety team

Enterprise On-Ramp vs Enterprise: which plan has a designated TAM and a 15-minute business-critical response?::Enterprise Support
