---
tags:
  - flashcards/services
---
# Flashcards: Services C (Management, Networking, Security)

Reference notes: [[Services - Management and Governance]], [[Services - Networking and Content Delivery]], [[Services - Security, Identity, and Compliance]].

## Management and Governance

A company wants one place to configure scaling for EC2 Auto Scaling groups, ECS tasks, DynamoDB capacity, and Aurora replicas together. Which service?::AWS Auto Scaling (scaling plans)

Automatically adding capacity when demand rises and removing it when demand falls is an example of which cloud benefit?::Elasticity

A team wants to deploy identical infrastructure in several Regions from a YAML template. Which service?::AWS CloudFormation

In CloudFormation, what is the collection of resources created from one template called?::A stack

An administrator needs to find out which IAM user terminated an EC2 instance yesterday. Which service?::AWS CloudTrail

How many days of management events does CloudTrail Event history show by default without creating a trail?::90 days

To keep CloudTrail logs longer than the default event history, where does a trail deliver them?::An Amazon S3 bucket

A team wants an alarm when an EC2 instance's CPU utilization stays above 80%. Which service?::Amazon CloudWatch

CloudWatch vs CloudTrail in one line each::CloudWatch = performance metrics, logs, and alarms; CloudTrail = who made which API call, when

Which service uses machine learning on utilization history to recommend the right EC2 instance type and size?::AWS Compute Optimizer

Compute Optimizer vs Trusted Advisor for rightsizing::Compute Optimizer gives deep ML sizing for compute only (EC2, ASGs, EBS, Lambda); Trusted Advisor gives broad best-practice checks across many categories

A company must see what a security group's rules were three weeks ago and be alerted if any S3 bucket becomes public. Which service?::AWS Config

Config vs CloudTrail::Config records resource configuration state, history, and rule compliance; CloudTrail records the API calls and who made them

A company wants to set up a secure, best-practice multi-account landing zone quickly with automated account provisioning. Which service?::AWS Control Tower

What are the three kinds of Control Tower controls (guardrails)?::Preventive; detective; proactive

Control Tower vs AWS Organizations::Organizations is the underlying account grouping, SCP, and consolidated billing service; Control Tower automates a best-practice landing zone on top of it

Where do you check whether an ongoing AWS service event or scheduled maintenance affects your own resources?::AWS Health Dashboard (your account health view)

Health Dashboard service health view vs account health view::Service health is the public status of all AWS services for everyone; account health shows events affecting your specific resources

Which support plans include programmatic access to the AWS Health API (exam plan names)?::Business, Enterprise On-Ramp, and Enterprise

A team wants a guided wizard to size and deploy SAP or Microsoft SQL Server on AWS following best practices. Which service?::AWS Launch Wizard

A company bringing its own Oracle and Microsoft licenses needs to track usage and prevent license violations. Which service?::AWS License Manager

A new user wants to manage AWS resources through a point-and-click web interface. Which tool?::AWS Management Console

A company wants one bill for 40 AWS accounts and to combine usage for volume discounts. Which service and feature?::AWS Organizations consolidated billing

What do service control policies (SCPs) do?::Set the maximum permissions for accounts or OUs in AWS Organizations; they never grant permissions

An administrator must add a CostCenter tag to hundreds of existing resources across Regions at once. Which tool?::Tag Editor (AWS Resource Groups and Tag Editor)

A company wants developers to launch only IT-approved, preconfigured products built from CloudFormation templates. Which service?::AWS Service Catalog

Service Catalog vs AWS Marketplace::Service Catalog is your organization's internal list of approved products; Marketplace is a public catalog of third-party software to buy

Which Systems Manager capability gives shell access to EC2 instances without SSH keys, bastion hosts, or open inbound port 22?::Session Manager

Which Systems Manager capability stores configuration values and secrets, with optional KMS encryption?::Parameter Store

Which Systems Manager capability automates OS patching across a fleet of EC2 and on-premises servers?::Patch Manager

A company wants automated recommendations about idle resources, open security group ports, root MFA, and service quotas. Which service?::AWS Trusted Advisor

Name the AWS Trusted Advisor check categories::Cost optimization; performance; security; fault tolerance; service limits (quotas); operational excellence

Which Trusted Advisor checks do Basic and Developer Support customers get?::Core checks only: service quotas plus basic security checks

A team wants to answer questions about one workload and compare it with the six Well-Architected pillars. Which service?::AWS Well-Architected Tool

Trusted Advisor vs Well-Architected Tool::Trusted Advisor automatically scans your account; Well-Architected Tool is a self-assessment questionnaire about a workload's design

## Networking and Content Delivery

A developer needs a managed front door that exposes Lambda functions as a REST API with throttling and authorization. Which service?::Amazon API Gateway

Which three API types can Amazon API Gateway create?::REST APIs; HTTP APIs; WebSocket APIs

A media site wants to cache images and video at edge locations close to global users to reduce latency. Which service?::Amazon CloudFront

Which DDoS protection does CloudFront include at no extra cost?::AWS Shield Standard

A company needs a private, dedicated connection from its data center to AWS with consistent performance that avoids the public internet. Which service?::AWS Direct Connect

Is AWS Direct Connect traffic encrypted by default, and how do you add encryption?::No; run a Site-to-Site VPN over it (or use MACsec on supported links)

A gaming company needs two fixed static IP addresses and fast Regional failover for UDP traffic. Which service?::AWS Global Accelerator

CloudFront vs Global Accelerator::CloudFront caches HTTP(S) content at the edge; Global Accelerator does not cache, gives static anycast IPs, and routes TCP/UDP over the AWS backbone

A company wants to register a domain name and route users to the Region with the lowest latency. Which service?::Amazon Route 53

What are Route 53's three main functions?::Domain registration; DNS routing; health checking

Which Route 53 routing policy sends traffic to a standby site only when the primary fails a health check?::Failover routing

Which Route 53 routing policy splits traffic by percentage, for example 90/10 for testing?::Weighted routing

Which service provides a logically isolated virtual network where you define IP ranges and subnets?::Amazon VPC

Which VPC component lets instances in a private subnet reach the internet without accepting inbound connections?::NAT gateway

A company needs an encrypted connection from its office to a VPC that can be set up in minutes over the internet. Which service?::AWS Site-to-Site VPN (AWS VPN)

Which AWS VPN option connects individual remote employees' devices to AWS?::AWS Client VPN

In a Site-to-Site VPN, what is the gateway on the AWS side of a single VPC called, and on the customer side?::Virtual private gateway (AWS side); customer gateway (on premises)

Direct Connect vs VPN::Direct Connect is a private dedicated link (consistent, weeks to set up, not encrypted by default); VPN is an encrypted tunnel over the internet (minutes to set up, variable performance)

A company wants to connect 50 VPCs and its on-premises network through one central hub instead of a mesh of peering links. Which service?::AWS Transit Gateway

Transit Gateway vs VPC peering::Transit Gateway is a hub that connects many VPCs and on-premises networks; VPC peering is a one-to-one, non-transitive link between two VPCs

## Security, Identity, and Compliance

An auditor asks for AWS's SOC 2 report and PCI DSS attestation. Where does the customer download them?::AWS Artifact

Where does a customer accept a Business Associate Addendum (BAA) with AWS for HIPAA workloads?::AWS Artifact (Artifact Agreements)

A company wants to continuously and automatically collect evidence from its AWS accounts to prepare for its own PCI DSS audit. Which service?::AWS Audit Manager

Artifact vs Audit Manager::Artifact provides AWS's own compliance reports and agreements; Audit Manager collects evidence about your own AWS usage for your audits

A company needs free public SSL/TLS certificates for its Application Load Balancer, renewed automatically. Which service?::AWS Certificate Manager (ACM)

ACM vs KMS::ACM manages TLS certificates for encryption in transit; KMS manages keys for encryption at rest

Regulations require a dedicated, single-tenant hardware security module with keys controlled only by the customer. Which service?::AWS CloudHSM

KMS vs CloudHSM::KMS is fully managed, multi-tenant, and integrated with most services; CloudHSM is dedicated single-tenant hardware where the customer manages the keys

A mobile app needs sign-up, sign-in, and Google or Facebook login for millions of customers. Which service?::Amazon Cognito

Which Cognito component is a user directory for sign-up and sign-in, and which gives users temporary AWS credentials?::User pools (directory); identity pools (temporary AWS credentials)

After GuardDuty flags a compromised instance, which service helps analysts visualize activity and find the root cause?::Amazon Detective

A company wants to domain-join EC2 Windows instances to a managed Microsoft Active Directory in AWS. Which service?::AWS Directory Service (AWS Managed Microsoft AD)

Which Directory Service option redirects requests to an existing on-premises AD without storing directory data in AWS?::AD Connector

A company with 30 accounts wants to apply the same WAF rules and Shield Advanced protections to all of them centrally. Which service?::AWS Firewall Manager

What does AWS Firewall Manager require to be set up first?::AWS Organizations

A company wants continuous, agentless threat detection that spots compromised credentials and crypto-mining from account activity logs. Which service?::Amazon GuardDuty

Which three core data sources does GuardDuty analyze?::AWS CloudTrail events; VPC Flow Logs; DNS logs

An EC2 instance needs to read objects from S3 without storing access keys on the instance. What should you use?::An IAM role attached to the instance

What is the difference between an IAM user and an IAM role?::A user has long-term credentials for one person or app; a role is assumed to get temporary credentials

Employees need one sign-in to access many AWS accounts in the organization plus business apps, using the corporate identity provider. Which service?::AWS IAM Identity Center (AWS Single Sign-On)

IAM Identity Center vs Cognito::IAM Identity Center is single sign-on for your workforce (employees); Cognito is sign-in for customers of your apps

A company wants continuous scanning of EC2 instances, ECR container images, and Lambda functions for known software vulnerabilities (CVEs). Which service?::Amazon Inspector

Inspector vs GuardDuty::Inspector finds software vulnerabilities and network exposure in workloads; GuardDuty detects active threats from log analysis

A company wants to create, rotate, and control access to the keys that encrypt its EBS volumes and S3 objects. Which service?::AWS Key Management Service (AWS KMS)

Which AWS service logs every use of a KMS key for auditing?::AWS CloudTrail

A company must find which S3 buckets contain PII such as credit card or passport numbers. Which service?::Amazon Macie

Macie scans which storage service for sensitive data?::Amazon S3

A company wants managed stateful traffic filtering and intrusion prevention at the perimeter of its VPC. Which service?::AWS Network Firewall

Network Firewall vs WAF::Network Firewall filters network traffic for a whole VPC (IDS/IPS); WAF filters HTTP(S) requests to web apps at layer 7

A central networking account wants to share its VPC subnets and Transit Gateway with other accounts in the organization. Which service?::AWS Resource Access Manager (AWS RAM)

A company wants to stop hardcoding database passwords in code and rotate RDS credentials automatically. Which service?::AWS Secrets Manager

Secrets Manager vs Systems Manager Parameter Store::Secrets Manager has built-in automatic rotation (paid per secret); Parameter Store stores configuration and secrets without built-in rotation (free standard tier)

A security team wants one dashboard that aggregates GuardDuty, Inspector, and Macie findings across accounts and scores them against the CIS benchmark. Which service?::AWS Security Hub

Which AWS service must be enabled for Security Hub to run most of its security checks?::AWS Config

Which service protects AWS resources against DDoS attacks?::AWS Shield

Shield Standard vs Shield Advanced::Standard is automatic and free for layer 3/4 attacks; Advanced is paid, adds 24/7 Shield Response Team access, cost protection, and enhanced protection

A web application must block SQL injection and cross-site scripting attempts and requests from certain countries. Which service?::AWS WAF

At which OSI layer does AWS WAF operate?::Layer 7 (application layer, HTTP/HTTPS)

Name three resources AWS WAF can be attached to::Amazon CloudFront; Application Load Balancer; Amazon API Gateway (also AppSync and Cognito user pools)
