---
tags:
  - clf-c02
  - cheat-sheet
aliases:
  - Glossary
  - Acronyms
---
# Acronyms and Glossary

One line per term, alphabetized. Terms in **bold** are the ones most worth memorizing. For look-alike services see [[Commonly Confused Services]].

## A
- **ACL (access control list)**: list of allow/deny rules; in a VPC, a network ACL filters traffic at the subnet level (stateless).
- **ACM (AWS Certificate Manager)**: provisions, stores, and renews SSL/TLS certificates.
- **Agility**: ability to try ideas and deliver resources in minutes instead of weeks; a core cloud benefit ([[1.1 Benefits of the AWS Cloud]]).
- **AMI (Amazon Machine Image)**: template (OS plus software) used to launch an EC2 instance.
- **AMS (AWS Managed Services)**: AWS operates your infrastructure for you on an ongoing basis.
- **API (application programming interface)**: programmatic way to call a service; every AWS action is an API call, recorded by CloudTrail.
- **APN (AWS Partner Network)**: AWS program for consulting partners, system integrators, and ISVs.
- **AWS Artifact**: self-service portal for AWS compliance reports and agreements.
- **Auto Scaling**: adds or removes capacity automatically to match demand; provides elasticity.
- **AZ (Availability Zone)**: one or more discrete data centers with redundant power, networking, and connectivity within a Region; AZs do not share single points of failure.

## B
- **BAA (Business Associate Addendum)**: HIPAA agreement with AWS, accepted through AWS Artifact.
- **Bastion host**: hardened instance used to reach instances in private subnets (largely replaced by Systems Manager Session Manager).
- **Block storage**: data stored in fixed-size blocks on a volume (EBS, instance store).
- **BYOL (Bring Your Own License)**: using licenses you already own on AWS; may require Dedicated Hosts for server-bound licenses ([[1.4 Cloud Economics]]).

## C
- **CAF (AWS Cloud Adoption Framework)**: guidance organized into six perspectives: Business, People, Governance, Platform, Security, Operations ([[1.3 Migration Strategies and AWS CAF]]).
- **CapEx (capital expenditure)**: up-front spending on physical assets such as servers; the cloud trades it for OpEx.
- **CDN (content delivery network)**: network of edge caches; Amazon CloudFront.
- **CI/CD (continuous integration / continuous delivery)**: automated build, test, and release; CodePipeline with CodeBuild and CodeDeploy.
- **CIDR (Classless Inter-Domain Routing)**: notation for IP address ranges, such as 10.0.0.0/16 for a VPC.
- **CLI (AWS Command Line Interface)**: command-line tool to call AWS APIs.
- **Cloud-native / all-in cloud deployment**: all workloads run in the cloud.
- **Compliance program**: certifications and attestations AWS holds (SOC, PCI DSS, ISO 27001, FedRAMP, HIPAA eligibility); see AWS Compliance and AWS Artifact.
- **Consolidated billing**: AWS Organizations feature giving one bill for all accounts and combined usage for volume discounts.
- **Cost allocation tag**: tag activated in the Billing console so costs can be grouped by that tag in Cost Explorer and the CUR; AWS-generated or user-defined.
- **CUR (AWS Cost and Usage Report)**: the most detailed cost and usage data, delivered to S3.
- **Customer gateway**: the device or software appliance on the customer side of a Site-to-Site VPN.
- **CVE (Common Vulnerabilities and Exposures)**: public list of known software vulnerabilities; Amazon Inspector scans for them.

## D
- **Data sovereignty / residency**: legal requirement that data stay in a given country; a reason to choose a specific Region.
- **DDoS (distributed denial of service)**: flood of traffic meant to make a service unavailable; AWS Shield protects against it.
- **Dedicated Host**: physical EC2 server dedicated to you, with socket and core visibility for licensing.
- **Dedicated Instance**: EC2 instance on hardware dedicated to your account, without host-level visibility or control.
- **Direct Connect gateway**: lets one Direct Connect connection reach VPCs in multiple Regions.
- **DMS (AWS Database Migration Service)**: migrates and replicates data between databases with minimal downtime.
- **DNS (Domain Name System)**: translates names to IP addresses; Amazon Route 53.
- **DR (disaster recovery)**: restoring service after a major failure; strategies range from backup and restore to multi-site active-active.
- **Durability**: likelihood that stored data is not lost; S3 is designed for 99.999999999% (11 nines).

## E
- **EBS (Amazon Elastic Block Store)**: persistent block volumes for EC2 in one AZ.
- **EC2 (Amazon Elastic Compute Cloud)**: resizable virtual servers (instances).
- **ECR (Amazon Elastic Container Registry)**: container image registry.
- **ECS (Amazon Elastic Container Service)**: AWS-native container orchestration.
- **Economies of scale**: AWS's huge aggregate usage lowers its costs, passed on as lower prices.
- **Edge location**: site used by CloudFront, Route 53, Global Accelerator, and Shield to serve users with low latency.
- **EFS (Amazon Elastic File System)**: serverless, elastic NFS file system shared across instances and AZs.
- **EKS (Amazon Elastic Kubernetes Service)**: managed Kubernetes.
- **Elasticity**: automatically scaling resources out and in as demand changes, paying only for what is used.
- **ELB (Elastic Load Balancing)**: distributes traffic across targets in multiple AZs; types include Application (ALB, layer 7), Network (NLB, layer 4), and Gateway Load Balancer.
- **EMR (Amazon EMR)**: managed Hadoop, Spark, and other big data frameworks.
- **Encryption at rest**: encrypting stored data (EBS, S3, RDS with KMS keys).
- **Encryption in transit**: encrypting data moving over a network (TLS/HTTPS, IPsec VPN).
- **ESG (environmental, social, and governance)**: improved ESG performance is one of the AWS CAF business outcomes.
- **ETL (extract, transform, load)**: preparing data for analytics; AWS Glue.

## F
- **Fault tolerance**: ability to keep operating with no interruption when a component fails.
- **Federation**: letting users sign in with an external identity provider (corporate directory, SAML 2.0, OIDC, social login) instead of IAM users.
- **FedRAMP**: US government cloud security authorization program.
- **FIPS 140**: US standard for cryptographic modules; CloudHSM and KMS HSMs are validated against it.
- **Fixed cost**: cost that does not change with usage, such as owned servers and data center leases.

## G
- **GDPR (General Data Protection Regulation)**: EU data protection law.
- **GraphQL**: API query language; AWS AppSync.
- **Guest OS**: the operating system on an EC2 instance; the customer patches it.

## H
- **High availability**: designing so a system stays accessible with minimal downtime, typically by running in multiple AZs.
- **HIPAA**: US health data law; many AWS services are HIPAA eligible under a BAA.
- **HPC (high performance computing)**: tightly coupled large-scale compute; FSx for Lustre, compute optimized instances.
- **HSM (hardware security module)**: tamper-resistant device for keys; AWS CloudHSM gives you a dedicated one.
- **Hybrid deployment**: on-premises infrastructure connected to cloud resources.
- **Hypervisor**: software that runs virtual machines on a host; securing it is AWS's responsibility.

## I
- **IaaS (infrastructure as a service)**: you rent compute, storage, network building blocks and manage the OS up (EC2).
- **IaC (infrastructure as code)**: defining infrastructure in templates; AWS CloudFormation.
- **IAM (AWS Identity and Access Management)**: users, groups, roles, and policies for access to AWS.
- **IAM group**: collection of IAM users that share permissions; groups cannot be nested and cannot be principals in a policy.
- **IAM policy**: JSON document that allows or denies actions on resources; AWS managed, customer managed, or inline.
- **IAM role**: identity with permissions and temporary credentials that users, services, or other accounts assume.
- **IAM user**: identity with long-term credentials for one person or application.
- **IDS/IPS (intrusion detection / prevention system)**: AWS Network Firewall provides this for a VPC.
- **Instance store**: temporary block storage physically attached to the EC2 host; data lost on stop or termination.
- **Internet gateway**: VPC component that allows communication between the VPC and the internet.
- **IoT (Internet of Things)**: connected devices; AWS IoT Core and IoT Greengrass.
- **IQ (AWS IQ)**: marketplace for hiring AWS Certified freelancers.
- **ISV (independent software vendor)**: company that builds and sells software, often through AWS Marketplace.

## K
- **KMS (AWS Key Management Service)**: create and control encryption keys.

## L
- **Landing zone**: well-architected multi-account baseline; set up by AWS Control Tower.
- **Latency**: delay between request and response; reduced by choosing nearby Regions, edge locations, Local Zones.
- **Least privilege**: grant only the permissions required to do a task.
- **Lifecycle policy**: S3 rules that transition objects to cheaper classes or expire them after a set time.
- **Local Zone**: AWS infrastructure in a large metro area for single-digit millisecond latency.

## M
- **Managed service**: AWS runs the infrastructure, patching, and scaling (RDS, DynamoDB, ECS, EKS).
- **MFA (multi-factor authentication)**: password plus a second factor (virtual app, hardware key, FIDO security key); always enable on the root user.
- **Migration strategies (7 Rs)**: retire, retain, rehost, relocate, repurchase, replatform, refactor ([[Migration Strategies (7 Rs)]]).
- **MQTT**: lightweight IoT messaging protocol used by AWS IoT Core.
- **MSK (Amazon Managed Streaming for Apache Kafka)**: managed Kafka.
- **Multi-AZ**: deploying across two or more AZs for high availability (for example, RDS Multi-AZ standby).

## N
- **NACL (network ACL)**: stateless subnet-level firewall with allow and deny rules.
- **NAT gateway**: lets instances in a private subnet reach the internet while blocking inbound connections from it.
- **NFS (Network File System)**: Linux file-sharing protocol; EFS.
- **NLP (natural language processing)**: understanding text; Comprehend, Kendra, Lex.
- **NoSQL**: non-relational databases (key-value, document, graph); DynamoDB, Neptune.

## O
- **Object storage**: data stored as objects with metadata and a key in a flat namespace; S3.
- **OLAP / OLTP**: analytical queries over large data sets (Redshift) vs many small transactions (RDS, Aurora).
- **On-Demand Capacity Reservation**: reserves EC2 capacity in an AZ with no term commitment; billed at On-Demand rates whether used or not.
- **On-premises**: infrastructure in your own data center (also called private cloud when virtualized).
- **OpEx (operational expenditure)**: ongoing pay-as-you-go spending.
- **OU (organizational unit)**: group of accounts within AWS Organizations to which SCPs can be applied.
- **Outposts**: AWS-managed racks running AWS services in your data center.

## P
- **PaaS (platform as a service)**: you provide code; the provider runs the platform (Elastic Beanstalk).
- **Pay-as-you-go**: pay only for what you use, with no long-term contract.
- **PCI DSS**: payment card industry security standard.
- **PII (personally identifiable information)**: data that identifies a person; Amazon Macie finds it in S3.
- **Pillars**: the six areas of the Well-Architected Framework: operational excellence, security, reliability, performance efficiency, cost optimization, sustainability.
- **Principal**: an entity (user, role, service, account) that can make a request in AWS.
- **Private subnet**: subnet with no route to an internet gateway.
- **Public subnet**: subnet whose route table sends internet traffic to an internet gateway.

## R
- **RAM (AWS Resource Access Manager)**: share resources such as subnets or Transit Gateways across accounts.
- **RDS (Amazon Relational Database Service)**: managed relational databases.
- **re:Post**: AWS community question-and-answer site.
- **Region**: isolated geographic area containing multiple AZs; choose by compliance, latency, service availability, and price.
- **Reliability**: ability of a workload to perform its function correctly and consistently, including recovering from failure.
- **Reserved Instance (RI)**: 1- or 3-year commitment to an instance configuration for a discount of up to 72%; Standard or Convertible; payment All Upfront, Partial Upfront, or No Upfront.
- **Rightsizing**: matching instance type and size to actual workload needs to reduce cost; AWS Compute Optimizer.
- **Root user**: identity created with the account (email and password) with full access; protect with MFA and do not use daily.
- **Route table**: rules that determine where network traffic from a subnet goes.
- **RPO / RTO (recovery point / recovery time objective)**: maximum acceptable data loss / downtime after a disaster.

## S
- **S3 (Amazon Simple Storage Service)**: object storage; 11 nines durability.
- **SaaS (software as a service)**: complete application delivered over the internet.
- **Savings Plans**: commit to a consistent $/hour of usage for 1 or 3 years for up to 72% off; Compute Savings Plans also cover Fargate and Lambda.
- **Scalability**: ability to handle growth by adding resources (vertical: bigger instance; horizontal: more instances).
- **SCP (service control policy)**: AWS Organizations policy that sets the maximum permissions for accounts in an OU; it grants nothing by itself.
- **SCT (AWS Schema Conversion Tool)**: converts database schema between engines.
- **SDK (software development kit)**: language libraries for calling AWS APIs from code.
- **Security group**: stateful virtual firewall at the instance level with allow rules only.
- **Serverless**: no servers to provision or manage, automatic scaling, pay for use (Lambda, Fargate, DynamoDB, S3).
- **Service quota (service limit)**: maximum number of a resource per account per Region; Trusted Advisor checks them.
- **SES (Amazon Simple Email Service)**: send and receive email.
- **Shared responsibility model**: AWS secures the cloud (hardware, facilities, global infrastructure); the customer secures what it puts in the cloud (data, IAM, OS, configuration) ([[2.1 Shared Responsibility Model]]).
- **SMB (Server Message Block)**: Windows file-sharing protocol; FSx for Windows File Server.
- **SNS (Amazon Simple Notification Service)**: pub/sub notifications.
- **SOC (System and Organization Controls) reports**: third-party audit reports on AWS controls, downloaded through AWS Artifact.
- **Spot Instance**: unused EC2 capacity at up to 90% off; can be interrupted with a two-minute warning.
- **SQL (Structured Query Language)**: language for relational databases; also used by Athena and Redshift.
- **SQS (Amazon Simple Queue Service)**: message queue for decoupling.
- **SSO (single sign-on)**: one sign-in for many accounts and apps; AWS IAM Identity Center (AWS Single Sign-On).
- **Stateful / stateless**: stateful firewalls remember connections and allow return traffic (security groups); stateless ones evaluate each packet (NACLs).
- **Subnet**: range of IP addresses in a VPC, located in exactly one AZ.
- **Sustainability**: the sixth Well-Architected pillar, minimizing environmental impact.

## T
- **TAM (Technical Account Manager)**: designated AWS technical contact; Enterprise Support has a designated TAM, Enterprise On-Ramp a pool of TAMs.
- **TCO (total cost of ownership)**: full cost of running infrastructure, including power, cooling, space, staff, and hardware refresh.
- **TLS / SSL (Transport Layer Security)**: protocol for encryption in transit (HTTPS); certificates from ACM.
- **Transit Gateway**: hub that connects many VPCs and on-premises networks through one gateway.
- **Trust and Safety team**: AWS team to contact to report abuse of AWS resources (spam, port scanning, DDoS from AWS IPs).

## V
- **Variable cost**: cost that rises and falls with usage; the cloud turns infrastructure into a variable cost.
- **Virtual private gateway**: the AWS-side endpoint of a Site-to-Site VPN, attached to a VPC.
- **VPC (Amazon Virtual Private Cloud)**: logically isolated virtual network in a Region.
- **VPC endpoint**: private connection from a VPC to supported AWS services without using the internet.
- **VPC Flow Logs**: capture IP traffic information for network interfaces in a VPC.
- **VPC peering**: private connection between two VPCs.
- **VPN (virtual private network)**: encrypted tunnel; AWS Site-to-Site VPN (networks) and AWS Client VPN (users).

## W
- **WAF (AWS WAF)**: web application firewall filtering HTTP(S) requests.
- **Wavelength Zone**: AWS infrastructure embedded in 5G carrier networks for ultra-low latency to mobile devices.
- **Well-Architected Framework**: AWS best-practice framework built on six pillars ([[Well-Architected and CAF]]).
- **Whitepaper**: AWS technical document, found on the AWS Whitepapers and Guides page.

## Numbers worth memorizing
- S3 durability 99.999999999% (11 nines); S3 Standard designed for 99.99% availability, Standard-IA 99.9%, One Zone-IA 99.5%.
- Minimum storage duration: Standard-IA and One Zone-IA 30 days; Glacier Instant Retrieval and Glacier Flexible Retrieval 90 days; Glacier Deep Archive 180 days.
- RIs and Savings Plans up to 72% off On-Demand; Spot up to 90% off; terms are 1 or 3 years.
- Lambda maximum run time 15 minutes.
- Support response for business-critical system down: Enterprise under 15 minutes, Enterprise On-Ramp under 30 minutes; production system down under 1 hour on Business and above ([[Support Plans]]).

Current status: AWS stopped selling Developer and Business Support to new subscribers on December 2, 2025, and those plans and Enterprise On-Ramp end on January 1, 2027; the current plans page lists Basic, Business Support+, Enterprise, and Unified Operations. The exam uses the five plans in the exam guide.
