---
tags:
  - flashcards/domain-2
---
# Flashcards - Domain 2: Security and Compliance

Study notes: [[2.1 Shared Responsibility Model]] · [[2.2 Security, Governance, and Compliance Concepts]] · [[2.3 Access Management and IAM]] · [[2.4 Security Components and Resources]]

## 2.1 Shared responsibility model

In the shared responsibility model, what is AWS responsible for?::Security OF the cloud (infrastructure, hardware, software, networking, facilities that run AWS services)

In the shared responsibility model, what is the customer responsible for?::Security IN the cloud (their data, identities, and configuration of the services they use)

Who patches the guest operating system of an EC2 instance?::The customer

Who patches the operating system of an Amazon RDS DB instance?::AWS

Who patches Elastic Load Balancers?::AWS

Who patches the operating system used by AWS Lambda?::AWS

Who secures the EC2 hypervisor?::AWS

Who is responsible for physical and environmental controls of data centers?::AWS

Who is responsible for edge location management?::AWS

Who is responsible for hardware maintenance?::AWS

Which party performs server-side encryption in Amazon S3, according to the reference guide?::AWS

Who is responsible for client-side data encryption and integrity?::The customer

Who sets IAM password policies?::The customer

Who configures security groups and network ACLs?::The customer ("configure firewalls and networks")

Who configures IAM roles?::The customer

Who determines which services have access to a DynamoDB table?::The customer

What three items does the reference guide list as shared responsibilities?::Patches; configuration; training and awareness

What is an inherited control? Give the example.::A control the customer fully inherits from AWS; physical and environmental controls

What is a shared control? Give the three examples.::A control that applies to both the AWS infrastructure layer and the customer layer; patch management, configuration management, awareness and training

What is a customer-specific control? Give the example.::A control that is solely the customer's responsibility; service and communications protection or zone security

How is patch management split as a shared control?::AWS patches the infrastructure; the customer patches their guest OS and applications

How is awareness and training split as a shared control?::AWS trains AWS employees; the customer trains its own employees

As you move from EC2 to RDS to Lambda, how does customer responsibility change?::It shrinks; AWS takes over OS, platform, and runtime management

When moving a database from EC2 to Amazon RDS, which tasks move to AWS?::OS and database engine patching, automated backups, and the underlying host management

With AWS Lambda, what remains the customer's responsibility?::Function code and its dependencies, IAM permissions (execution role), and data

Which responsibilities never move to AWS regardless of service?::Customer data, its classification and encryption choices, and IAM access permissions

Who is responsible for the security of data stored in an S3 bucket set to public access?::The customer

## 2.2 Security, governance, and compliance concepts

What are the two parts of AWS Artifact?::Artifact Reports (audit reports) and Artifact Agreements (such as the HIPAA BAA)

Where do you accept a Business Associate Addendum (BAA) with AWS?::AWS Artifact (Artifact Agreements)

Which AWS website explains compliance programs by region and industry?::AWS Compliance (aws.amazon.com/compliance)

Where do you check whether a specific AWS service is covered by a compliance program?::AWS Services in Scope by Compliance Program page

Does AWS holding a PCI DSS attestation make a customer's application PCI compliant?::No; the customer must still configure and run its workload to meet the requirements

What does encryption at rest protect?::Stored data (disks, databases, backups, S3 objects)

What does encryption in transit protect, and with what protocol?::Data moving over the network; TLS (HTTPS), or IPsec for Site-to-Site VPN

KMS vs CloudHSM: which one is single-tenant and fully customer-managed?::CloudHSM

What is the default encryption for new objects uploaded to S3 since January 2023?::SSE-S3 (server-side encryption with Amazon S3 managed keys)

Which S3 encryption option uses keys stored in AWS KMS?::SSE-KMS

Which S3 encryption option has the customer supply the key with each request?::SSE-C

How long does CloudTrail event history keep management events by default?::90 days

How do you keep CloudTrail logs longer than 90 days?::Create a trail that delivers log files to an S3 bucket

Which service records configuration history of resources and evaluates them against rules?::AWS Config

Which feature captures IP traffic information for network interfaces in a VPC?::VPC Flow Logs

Where can VPC Flow Logs be published?::CloudWatch Logs, Amazon S3, or Amazon Data Firehose

Which feature records detailed requests made to an S3 bucket?::S3 server access logs

CloudTrail vs Config: which answers "who changed it" and which answers "what did it look like"?::CloudTrail answers who; Config answers what it looked like and how it changed

Which service continuously collects evidence to prepare for your own audits against frameworks like PCI DSS or HIPAA?::AWS Audit Manager

Artifact vs Audit Manager?::Artifact gives AWS's own compliance reports; Audit Manager gathers evidence about your AWS usage

Which access report lists every IAM user and the status of their passwords, keys, and MFA?::IAM credential report

Which access report shows which services an identity used and when?::IAM access advisor (last accessed information)

GuardDuty vs Inspector?::GuardDuty detects active threats from logs; Inspector finds software vulnerabilities and network exposure in workloads

Security Hub vs Detective?::Security Hub collects and prioritizes findings; Detective investigates the root cause

## 2.3 Access management and IAM

Is IAM a global or regional service, and what does it cost?::Global; no additional charge

What is the principle of least privilege?::Grant only the permissions needed to perform a task, nothing more

In IAM policy evaluation, what overrides everything else?::An explicit Deny

What is the default IAM decision when no policy allows an action?::Implicit deny

What kind of credentials does an IAM role provide?::Temporary security credentials from AWS STS

What kind of credentials does an IAM user have?::Long-term credentials (password and/or access keys)

What is the best way to let an EC2 application access S3?::Attach an IAM role to the instance

Can an IAM group contain other groups?::No; groups contain only users

What is an IAM group used for?::Attaching permissions to many users at once by job function

What are the three identity-based policy types by ownership?::AWS managed, customer managed, inline

Which policy type is reusable and written by you for least privilege?::Customer managed policy

What is an inline policy?::A policy embedded in a single user, group, or role, deleted with it

What is a resource-based policy? Give an example.::A policy attached to a resource naming who can access it; S3 bucket policy

What sets the maximum permissions for accounts in AWS Organizations?::Service control policies (SCPs)

What are the two most important root user protections?::Enable MFA; do not create root access keys

Should the root user be used for daily administrative tasks?::No; create an administrative identity and use root only for root-only tasks

Name the root-only task for account closure and account settings.::Close the account; change the root email address, root password, or root access keys

Who can restore permissions when the only IAM admin locks themselves out?::The root user

Which root-only task relates to billing access?::Activating IAM user and role access to the Billing and Cost Management console

Which root-only task relates to the Reserved Instance Marketplace?::Registering as a seller

Which root-only task relates to S3 versioning protection?::Enabling MFA Delete on an S3 bucket

Which root-only task relates to a locked-out S3 bucket?::Editing or deleting a bucket policy that denies all principals

Which root-only task relates to AWS GovCloud (US)?::Signing up for GovCloud (US)

What does an IAM password policy control?::Minimum length, character requirements, expiration, reuse prevention, and self-service changes for IAM users

What are access keys used for?::Programmatic access (CLI, SDKs, APIs): access key ID plus secret access key

Name three MFA device types AWS supports.::Virtual authenticator app; passkey or FIDO2 security key; hardware TOTP token

What is federation?::Letting users sign in with an external identity provider and receive temporary AWS credentials, without IAM users

Which service gives the workforce single sign-on to multiple AWS accounts and business apps?::AWS IAM Identity Center (AWS Single Sign-On)

Cognito user pools vs identity pools?::User pools are a user directory for sign-up and sign-in; identity pools exchange identities for temporary AWS credentials

How do users in one account access resources in another account without new IAM users?::Cross-account IAM role

Which Systems Manager capability stores configuration data and secrets, with a free standard tier?::Parameter Store

Secrets Manager vs Parameter Store: which has built-in rotation?::Secrets Manager

Which tool finds resources shared with entities outside your account or organization?::IAM Access Analyzer

Identity Center vs Cognito?::Identity Center is for employees accessing AWS accounts and apps; Cognito is for customers of your application

## 2.4 Security components and resources

Security group: stateful or stateless?::Stateful

Network ACL: stateful or stateless?::Stateless

At what level does a security group operate?::Instance level (network interface)

At what level does a network ACL operate?::Subnet level

Which firewall supports only allow rules?::Security group

Which firewall supports both allow and deny rules?::Network ACL

How are network ACL rules evaluated?::In number order, lowest first; first match applies

What does a new custom security group allow by default?::No inbound traffic; all outbound traffic

What does the default network ACL in a VPC allow?::All inbound and outbound traffic

How do you block one specific IP address from a subnet?::Add a deny rule to the network ACL

Which resources can AWS WAF be attached to?::CloudFront, Application Load Balancer, API Gateway, AppSync, Cognito user pools

Which DDoS protection is free and automatic for all customers?::AWS Shield Standard

What does Shield Advanced add?::Larger and Layer 7 DDoS protection, 24/7 Shield Response Team, DDoS cost protection, attack visibility, WAF for protected resources

Which support plans are required to engage the Shield Response Team?::Business or Enterprise Support

What does Shield Advanced cost?::Starting at $3,000 per month with a one-year commitment, plus data transfer fees

Which service centrally manages WAF rules, Shield Advanced, and security groups across accounts?::AWS Firewall Manager

What does Firewall Manager require?::AWS Organizations

Shield vs WAF?::Shield stops DDoS floods; WAF filters malicious HTTP(S) requests

Where do you buy third-party security software such as firewall appliances to run on AWS?::AWS Marketplace

Which resource has articles answering the questions AWS Support receives most often?::AWS Knowledge Center (on AWS re:Post)

Which AWS web page is the main hub for AWS security information and security bulletins?::AWS Security Center (aws.amazon.com/security)

Where do AWS experts publish security best practices and feature announcements?::AWS Security Blog

Name the core Trusted Advisor security checks available to all customers.::S3 bucket permissions; security groups specific ports unrestricted; MFA on root account; EBS public snapshots; RDS public snapshots

Which support plans get all Trusted Advisor checks?::Business, Enterprise On-Ramp, and Enterprise

Which Well-Architected pillar gives best practices for protecting data, systems, and assets?::Security pillar
