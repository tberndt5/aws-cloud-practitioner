---
tags:
  - clf-c02
  - practice
  - mock-exam
---
# Mock Exam 2

> [!info] Instructions
> - **65 questions, 90 minutes, closed book.** Set a timer and do not open the answers until you finish all 65.
> - This exam tests the same blueprint as [[Mock Exam 1]] with entirely different questions. It is slightly harder: many questions have two options that look right until one word in the stem (most cost-effective, least operational overhead, fully managed, dedicated, no commitment) decides it. Read every qualifier.
> - The real exam scores 50 questions and includes 15 unscored ones you cannot identify, reported as a scaled score of 100–1,000. **700 passes**, roughly 70% correct. Your target here is **90% (59 of 65)**.
> - There is no penalty for guessing. Never leave a question blank.
> - "Select TWO" questions need both correct answers to score. There are 10 of them.
> - Domain weighting matches the exam guide: Domain 1 = 16 questions, Domain 2 = 19, Domain 3 = 22, Domain 4 = 8, interleaved as on the real exam.
> - When you finish, mark each answer right or wrong in the [[#Scoring table]] and total each domain. Reread the task note linked in each Review line for every miss.

> [!note] Support plan names
> This exam uses the support plans in the CLF-C02 exam guide (Basic, Developer, Business, Enterprise On-Ramp, Enterprise). Current status: AWS stopped selling Developer and Business Support to new subscribers on December 2, 2025, and those plans and Enterprise On-Ramp end on January 1, 2027 (replaced by Business Support+, Enterprise, and Unified Operations). The exam still tests the older names.

---

### Q1
A company runs an in-memory analytics engine that loads a multi-terabyte data set entirely into RAM so it can answer real-time queries. Which EC2 instance category is the best fit?

- A. General purpose
- B. Compute optimized
- C. Memory optimized
- D. Storage optimized

> [!success]- Answer
> **C.** Memory optimized instances are designed for workloads that process large data sets in memory, such as in-memory databases and real-time big data analytics.
> - A: General purpose instances balance compute, memory, and networking for workloads such as web servers; they do not offer the large memory-to-CPU ratio this needs.
> - B: Compute optimized instances suit CPU-bound work such as batch processing and media transcoding.
> - D: Storage optimized instances suit high, sequential read and write access to large data sets on local storage, not holding data in RAM.
>
> Review: [[3.3 Compute Services]]

### Q2
Amazon GuardDuty reports that an IAM role's credentials were used from an unusual location. A security analyst must now find the root cause by viewing the related activity over time across the role, the source IP addresses, and the EC2 instances involved, without building a log analysis system. Which service should the analyst use?

- A. Amazon GuardDuty
- B. Amazon Detective
- C. AWS Security Hub
- D. Amazon Inspector

> [!success]- Answer
> **B.** Detective analyzes and visualizes log data so analysts can investigate the root cause of security findings or suspicious activity.
> - A: GuardDuty detected the threat and created the finding; investigating its root cause is Detective's job.
> - C: Security Hub aggregates and prioritizes findings and runs best-practice checks; it is not an investigation tool.
> - D: Inspector scans workloads for software vulnerabilities.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q3
A company's IT staff spend most of their time racking servers, replacing failed disks, and managing data center power and cooling. Leadership wants that effort redirected to building features that customers will notice. Which advantage of cloud computing does this describe?

- A. Stop spending money running and maintaining data centers
- B. Benefit from massive economies of scale
- C. Trade fixed expense for variable expense
- D. Go global in minutes

> [!success]- Answer
> **A.** Moving to AWS removes the undifferentiated heavy lifting of running data centers, so staff can focus on customers and products.
> - B: Economies of scale explain why AWS's prices are low; the stem is about where staff spend their time.
> - C: Trading fixed for variable expense is about paying only for what you use, not about freeing staff from data center work.
> - D: Going global in minutes is about deploying in other parts of the world quickly.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q4
An online store must send order confirmation emails and a monthly newsletter to its customers from the store's own domain, and track bounces and complaints. Which service should it use?

- A. Amazon Simple Notification Service (Amazon SNS)
- B. Amazon Connect
- C. Amazon Simple Queue Service (Amazon SQS)
- D. Amazon Simple Email Service (Amazon SES)

> [!success]- Answer
> **D.** SES sends transactional and marketing email from your own email addresses and domains, with bounce and complaint tracking.
> - A: SNS pushes notifications to subscribers who opted in to a topic; it is not built for sending branded transactional and marketing email from your domain.
> - B: Connect is a cloud contact center for customer calls and chats.
> - C: SQS is a message queue between software components; it does not send email.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q5
A company places an Application Load Balancer in front of its EC2 instances. Under the AWS shared responsibility model, which task is AWS's responsibility?

- A. Defining the listener rules that route requests to target groups
- B. Patching and maintaining the software that runs the load balancer
- C. Choosing which security groups are attached to the load balancer
- D. Selecting the TLS certificate that the HTTPS listener presents

> [!success]- Answer
> **B.** Elastic Load Balancing is a managed service, and AWS patches the load balancers themselves.
> - A: Routing rules are the customer's configuration.
> - C: Security group configuration is always the customer's responsibility.
> - D: The customer chooses and attaches the certificate, even when ACM issues and renews it.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q6
A retailer must be certain it can launch 40 m5.xlarge instances in one specific Availability Zone during a two-week holiday event. It will not make any commitment that lasts beyond the event. Which option guarantees this capacity?

- A. On-Demand Capacity Reservations
- B. Zonal Reserved Instances
- C. Spot Instances
- D. Compute Savings Plans

> [!success]- Answer
> **A.** On-Demand Capacity Reservations reserve EC2 capacity in a specific Availability Zone for any duration, with no term commitment. You pay On-Demand rates for the reserved capacity whether or not instances run.
> - B: Zonal Reserved Instances reserve capacity but require a 1-year or 3-year term.
> - C: Spot Instances can be interrupted and guarantee no capacity.
> - D: Savings Plans give a discount for a 1-year or 3-year commitment and do not reserve capacity.
>
> Review: [[4.1 AWS Pricing Models]]

### Q7
A company's cloud team measures cost per customer order each month, tags every resource so each product team sees and owns its share of the bill, and replaces self-run servers with managed services so engineers stop spending time on work that does not differentiate the business. Which pillar of the AWS Well-Architected Framework do these practices represent?

- A. Sustainability
- B. Operational excellence
- C. Cost optimization
- D. Performance efficiency

> [!success]- Answer
> **C.** Measuring overall efficiency, analyzing and attributing expenditure, and stopping spending on undifferentiated heavy lifting are Cost optimization design principles.
> - A: Sustainability also favors managed services, but its goal is reducing energy use and environmental impact, not attributing spend to teams.
> - B: Operational excellence focuses on running and improving operations, such as operations as code and small reversible changes.
> - D: Performance efficiency focuses on using resources efficiently to meet performance requirements.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q8
A bank wants to detect fraud rings by querying relationships among accounts, devices, phone numbers, and transactions, often several hops deep, with millisecond response times. Which database service fits best?

- A. Amazon DynamoDB
- B. Amazon Aurora
- C. Amazon Redshift
- D. Amazon Neptune

> [!success]- Answer
> **D.** Neptune is a graph database built for highly connected data sets, such as fraud detection, social networks, and recommendation engines.
> - A: DynamoDB is a key-value and document database; it is not designed to traverse many relationships.
> - B: Aurora is relational; multi-hop relationship queries need many joins and are what graph databases are built to avoid.
> - C: Redshift is a data warehouse for analytical queries, not low-latency relationship traversal.
>
> Review: [[3.4 Database Services]]

### Q9
A company must inspect all traffic entering and leaving its VPCs, including non-HTTP protocols, using stateful rules and intrusion prevention that blocks known malicious traffic patterns. It wants an AWS managed service rather than running its own appliances. Which service should it use?

- A. AWS Network Firewall
- B. AWS WAF
- C. Security groups
- D. AWS Shield Advanced

> [!success]- Answer
> **A.** Network Firewall is a managed, stateful network firewall with intrusion detection and prevention for VPCs.
> - B: AWS WAF filters HTTP(S) requests to web applications only.
> - C: Security groups allow traffic by port, protocol, and source; they have no intrusion prevention and cannot block attack patterns.
> - D: Shield Advanced protects against DDoS attacks; it does not inspect all VPC traffic against intrusion rules.
>
> Review: [[2.4 Security Components and Resources]]

### Q10
A visual effects studio in Los Angeles needs single-digit millisecond latency between its artists' workstations and GPU instances used for rendering. The nearest AWS Region is several hundred miles away, and the studio does not want to install or house any AWS hardware in its own building. Which option should it use?

- A. AWS Outposts
- B. AWS Local Zones
- C. AWS Wavelength
- D. Amazon CloudFront

> [!success]- Answer
> **B.** Local Zones place AWS compute and storage close to large population and industry centers, such as Los Angeles, for low-latency access without hardware on the customer's premises.
> - A: Outposts would deliver low latency, but it installs AWS racks in the customer's own facility, which the studio does not want.
> - C: Wavelength serves mobile devices on 5G networks.
> - D: CloudFront caches content for delivery; it does not run rendering instances.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q11
A company migrates its applications from its data center to Linux EC2 instances. Its applications use a third-party commercial database that it licenses per core and brings to AWS under a Bring Your Own License (BYOL) model. Which TWO costs does the company continue to bear after the migration? (Select TWO.)

- A. Staff time to patch and maintain the guest operating systems
- B. Electricity and cooling for the servers
- C. The third-party database licenses it brings
- D. Replacing failed server hardware
- E. Physical security staff for the data center

> [!success]- Answer
> **A and C.** On EC2 the customer still manages the guest OS, and with BYOL the customer still pays for the licenses it brings.
> - B: Power and cooling are included in AWS's prices.
> - D: Hardware replacement is AWS's responsibility.
> - E: Physical security of AWS facilities is AWS's responsibility.
>
> Review: [[1.4 Cloud Economics]]

### Q12
The administrator of a new standalone AWS account wants IAM users on the finance team to use the Billing and Cost Management console. Their IAM policies already allow billing actions, but they still cannot see billing data. Which step requires signing in as the root user?

- A. Creating an IAM group for the finance team
- B. Attaching the Billing job function policy to the group
- C. Activating IAM user and role access to the Billing and Cost Management console
- D. Turning on AWS CloudTrail

> [!success]- Answer
> **C.** Activating IAM access to the Billing and Cost Management console is on AWS's list of tasks that require root user credentials. Until it is activated, IAM permissions alone do not grant access to billing data.
> - A: An IAM identity with IAM permissions can create groups.
> - B: An IAM administrator can attach policies; the stem says the permissions are already in place.
> - D: An IAM identity with the right permissions can create a trail.
>
> Review: [[2.3 Access Management and IAM]]

### Q13
Before migrating, a company wants to estimate the monthly cost of a planned architecture (12 EC2 instances, an Amazon RDS Multi-AZ database, and 5 TB in Amazon S3) and share a link to the estimate with its finance team. It has no AWS usage yet. Which tool should it use?

- A. AWS Cost Explorer
- B. AWS Budgets
- C. AWS Cost and Usage Report
- D. AWS Pricing Calculator

> [!success]- Answer
> **D.** Pricing Calculator estimates the cost of resources you plan to use and produces a shareable estimate.
> - A: Cost Explorer analyzes and forecasts from actual past usage, and this company has none yet.
> - B: Budgets alerts on actual or forecasted spend against a threshold.
> - C: The Cost and Usage Report details actual usage that has already occurred.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q14
A company has 40 VPCs across several accounts in one Region, plus an on-premises network connected by VPN. Managing hundreds of one-to-one connections between them has become unworkable. It wants a central hub that every VPC and the on-premises network attach to. What should it use?

- A. VPC peering
- B. AWS Transit Gateway
- C. A virtual private gateway
- D. An internet gateway

> [!success]- Answer
> **B.** Transit Gateway connects VPCs, AWS accounts, and on-premises networks through a single central gateway.
> - A: VPC peering is a one-to-one connection between two VPCs, which is the mesh the company wants to replace.
> - C: A virtual private gateway is the AWS side of a Site-to-Site VPN for one VPC; it is not a hub for many VPCs.
> - D: An internet gateway connects a VPC to the internet.
>
> Review: [[3.5 Network Services]]

### Q15
After a security incident, the team needs two kinds of records: which identity called which AWS APIs and from what IP address, and the operating system and application log files from its EC2 instances, stored centrally and searchable. Which TWO services provide these? (Select TWO.)

- A. AWS Config
- B. AWS CloudTrail
- C. AWS Artifact
- D. Amazon CloudWatch Logs
- E. AWS Trusted Advisor

> [!success]- Answer
> **B and D.** CloudTrail records API activity with the caller identity and source IP, and CloudWatch Logs collects, stores, and searches log files from instances and applications.
> - A: Config records resource configurations and their changes; it does not hold API call records or application log files.
> - C: Artifact provides AWS's compliance reports.
> - E: Trusted Advisor checks the account against best practices; it stores no logs.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q16
During migration planning, a company finds an application that was upgraded on premises last year, runs on hardware that is still being depreciated, and is not a business priority to move. It decides to keep the application where it is and revisit the decision in two years. Which migration strategy is this?

- A. Retire
- B. Rehost
- C. Retain
- D. Relocate

> [!success]- Answer
> **C.** Retain means keeping an application in its source environment for now, often because it was recently upgraded or is not ready to move.
> - A: Retire means decommissioning an application that is no longer needed; this one stays in use.
> - B: Rehost moves the application to AWS as is.
> - D: Relocate moves infrastructure, such as VMware workloads, to the cloud without changes; this application is not moving.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q17
A company backs up its servers to a physical tape library using its existing backup software. It wants to stop handling physical tapes and keep the backups durably in AWS, including archival in Amazon S3 Glacier storage classes, without changing its backup software or process. Which service meets this need?

- A. AWS Storage Gateway (Tape Gateway)
- B. AWS Snowball Edge
- C. Amazon Elastic File System (Amazon EFS)
- D. AWS Backup

> [!success]- Answer
> **A.** Tape Gateway presents virtual tapes to existing backup software and stores them in Amazon S3, archiving to S3 Glacier storage classes.
> - B: Snowball Edge is for one-time offline transfers or edge computing, not an ongoing replacement for a tape library.
> - C: EFS is a file system for Linux workloads, not a target that backup software sees as tapes.
> - D: AWS Backup centralizes backup policies, but adopting it means changing the backup software and process, which the company wants to avoid.
>
> Review: [[3.6 Storage Services]]

### Q18
An application needs a few configuration values stored centrally: a feature setting, an endpoint URL, and a license key, with the license key encrypted. None of the values need automatic rotation. The company wants the most cost-effective option. Which service should it use?

- A. AWS Secrets Manager
- B. AWS Key Management Service (AWS KMS)
- C. AWS Certificate Manager (ACM)
- D. AWS Systems Manager Parameter Store

> [!success]- Answer
> **D.** Parameter Store stores configuration data and secrets (encrypted as SecureString parameters), and standard parameters have no additional charge.
> - A: Secrets Manager would work, but it charges per secret, and its main advantage, automatic rotation, is not needed here.
> - B: KMS creates and controls encryption keys; it does not store application configuration values.
> - C: ACM manages SSL/TLS certificates.
>
> Review: [[2.3 Access Management and IAM]]

### Q19
An administrator on a locked-down corporate laptop cannot install software but needs to run a few AWS CLI commands right now. She wants a pre-authenticated shell that she can open directly from the AWS Management Console, with no environment to create first. What should she use?

- A. AWS Cloud9
- B. AWS CloudShell
- C. The AWS CLI installed on the laptop
- D. The AWS SDK for Python

> [!success]- Answer
> **B.** CloudShell is a browser-based, pre-authenticated shell launched from the console, with the AWS CLI already installed.
> - A: Cloud9 is an IDE that requires creating a development environment first.
> - C: She cannot install software on the laptop.
> - D: An SDK is a library for writing application code, not an interactive shell.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q20
Which TWO are design principles of the Cost optimization pillar of the AWS Well-Architected Framework? (Select TWO.)

- A. Use serverless architectures
- B. Maximize utilization
- C. Analyze and attribute expenditure
- D. Anticipate failure
- E. Stop spending money on undifferentiated heavy lifting

> [!success]- Answer
> **C and E.** Analyzing and attributing expenditure and stopping spending on undifferentiated heavy lifting are Cost optimization principles.
> - A: Use serverless architectures is a Performance efficiency principle.
> - B: Maximize utilization is a Sustainability principle, aimed at reducing energy use.
> - D: Anticipate failure is an Operational excellence principle.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q21
A developer is building a prototype on AWS that is not in production. She wants to ask AWS technical questions about errors and best practices and is fine with answers by web and email during business hours. Which is the lowest-cost support plan that provides technical support?

- A. Developer
- B. Basic
- C. Business
- D. Enterprise On-Ramp

> [!success]- Answer
> **A.** Developer Support provides business-hours web access to Cloud Support Associates, with general guidance within 24 business hours.
> - B: Basic includes customer service for account and billing questions only, with no technical support cases.
> - C: Business adds 24/7 phone, web, and chat and production response times, which she does not need and which cost more.
> - D: Enterprise On-Ramp costs much more and is aimed at production and business-critical workloads.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q22
AWS trains its own employees on security, and each customer must train its own employees. Under the AWS shared responsibility model, how is security awareness and training classified?

- A. An inherited control
- B. A customer-specific control
- C. A shared control
- D. An AWS-only responsibility, because AWS operates the infrastructure

> [!success]- Answer
> **C.** Awareness and training is a shared control: AWS and the customer each apply it within their own layer. Patch management and configuration management are the other shared controls.
> - A: Inherited controls are ones the customer fully inherits from AWS, such as physical and environmental controls.
> - B: Customer-specific controls are solely the customer's, such as zone security inside its own environments.
> - D: AWS cannot train the customer's staff for it.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q23
A company needs a MySQL-compatible relational database that AWS manages. It specifically wants storage that grows automatically and keeps six copies of its data across three Availability Zones. Which service should it choose?

- A. Amazon RDS for MySQL
- B. Amazon DynamoDB
- C. Amazon MemoryDB for Redis
- D. Amazon Aurora

> [!success]- Answer
> **D.** Aurora is MySQL- and PostgreSQL-compatible, and its storage grows automatically and keeps six copies of data across three Availability Zones.
> - A: RDS for MySQL is managed and relational, but it does not use Aurora's six-copy, three-AZ storage; a Multi-AZ deployment keeps a standby in one other Availability Zone.
> - B: DynamoDB is a NoSQL database, not MySQL-compatible.
> - C: MemoryDB is a Redis-compatible in-memory database, not relational.
>
> Review: [[3.4 Database Services]]

### Q24
A company runs a self-managed key-value database on 20 EC2 instances. Administrators spend many hours patching servers, replicating data across Availability Zones, and adding nodes as the data grows. Which option most reduces this operational work while keeping a key-value data model?

- A. Move the database to larger EC2 instances
- B. Migrate to Amazon DynamoDB
- C. Migrate to Amazon RDS for MySQL
- D. Purchase Reserved Instances for the 20 instances

> [!success]- Answer
> **B.** DynamoDB is a fully managed, serverless key-value database: AWS handles servers, patching, replication across Availability Zones, and scaling.
> - A: Larger instances still need patching, replication, and scaling by the administrators.
> - C: RDS is managed but relational, and the company would still choose and size instances.
> - D: Reserved Instances lower the price but do not reduce any operational work.
>
> Review: [[1.4 Cloud Economics]]

### Q25
A small company wants protection against common network and transport layer DDoS attacks, such as SYN floods and UDP reflection attacks, for its Amazon CloudFront distribution. It has no budget for additional security services. What protection does it have?

- A. AWS Shield Standard, which is applied automatically at no additional cost
- B. AWS Shield Advanced, which is included with every CloudFront distribution
- C. AWS WAF rate-based rules, which are free for all customers
- D. Amazon GuardDuty, which blocks DDoS traffic automatically

> [!success]- Answer
> **A.** Shield Standard protects all AWS customers against the most common network and transport layer DDoS attacks automatically, at no additional charge.
> - B: Shield Advanced is a paid subscription.
> - C: AWS WAF is charged per web ACL, rule, and request.
> - D: GuardDuty is a paid threat detection service that creates findings; it does not block traffic.
>
> Review: [[2.4 Security Components and Resources]]

### Q26
Which statement correctly describes the relationship among AWS Regions, Availability Zones, and edge locations?

- A. Each edge location contains several Regions, and each Region contains Availability Zones.
- B. An Availability Zone can span two Regions so that either Region can fail over to it.
- C. Each Region contains multiple isolated Availability Zones, and edge locations are separate sites, far more numerous than Regions, that services such as Amazon CloudFront and Amazon Route 53 use to serve users from nearby.
- D. Edge locations are Availability Zones reserved for running EC2 instances closer to users.

> [!success]- Answer
> **C.** Regions are made up of multiple Availability Zones, and the edge network is a much larger set of locations used by CloudFront, Route 53, and similar services to reduce latency.
> - A: Edge locations are small sites; they do not contain Regions.
> - B: Every Availability Zone belongs to exactly one Region.
> - D: Edge locations are not Availability Zones and do not host your EC2 instances.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q27
A company must move 300 on-premises virtual machines to AWS quickly, with no code changes and minimal downtime at cutover. It wants a service that continuously replicates the source servers to AWS and then launches them as EC2 instances. Which service should it use?

- A. AWS Database Migration Service (AWS DMS)
- B. AWS Schema Conversion Tool (AWS SCT)
- C. AWS Migration Hub
- D. AWS Application Migration Service

> [!success]- Answer
> **D.** Application Migration Service is AWS's automated lift-and-shift (rehost) service: it replicates whole servers continuously and launches them on EC2.
> - A: DMS migrates databases, not whole servers.
> - B: SCT converts database schemas between engines.
> - C: Migration Hub tracks migration progress across tools; it does not replicate servers itself.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q28
A company's compliance policy requires that its EC2 instances run on hardware not shared with any other AWS customer. It does not use per-socket or per-core licenses and needs no visibility into or control over the physical server. It wants to meet the requirement without paying for an entire physical server. Which option should it choose?

- A. Dedicated Hosts
- B. Dedicated Instances
- C. On-Demand Instances with default tenancy
- D. Spot Instances

> [!success]- Answer
> **B.** Dedicated Instances run on hardware dedicated to one customer, billed per instance, with no need to manage or pay for a whole host.
> - A: Dedicated Hosts also isolate hardware, but you pay for the entire physical server; they are chosen for socket and core visibility or server-bound licenses, which this company does not need.
> - C: Default tenancy runs on shared hardware.
> - D: Spot Instances run on shared hardware and can be interrupted.
>
> Review: [[4.1 AWS Pricing Models]]

### Q29
A support center records customer calls in Spanish and Portuguese. Management wants a written English version of every call. Which TWO services should be used together? (Select TWO.)

- A. Amazon Transcribe
- B. Amazon Polly
- C. Amazon Lex
- D. Amazon Translate
- E. Amazon Comprehend

> [!success]- Answer
> **A and D.** Transcribe converts the recorded speech to text, and Translate converts that text into English.
> - B: Polly does the opposite, turning text into speech.
> - C: Lex builds conversational chatbots.
> - E: Comprehend extracts sentiment, key phrases, and entities from text; it does not translate.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q30
A company stores customer documents in Amazon S3. Under the shared responsibility model, which task is the company's responsibility?

- A. Configuring bucket policies and S3 Block Public Access settings
- B. Storing redundant copies of objects across multiple Availability Zones
- C. Maintaining the disks that hold the objects
- D. Patching the software that runs the S3 service

> [!success]- Answer
> **A.** The customer controls who can access its data, which in S3 means bucket policies, access control settings, and Block Public Access.
> - B: S3 Standard stores data redundantly across Availability Zones automatically.
> - C: Hardware maintenance is AWS's responsibility.
> - D: AWS operates and patches the S3 service.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q31
What makes a subnet in an Amazon VPC a public subnet?

- A. It contains a NAT gateway.
- B. Its network ACL allows all inbound traffic.
- C. It is attached to a virtual private gateway.
- D. Its route table has a route to an internet gateway.

> [!success]- Answer
> **D.** A subnet is public when its route table sends internet-bound traffic to an internet gateway.
> - A: A NAT gateway is placed in a public subnet, but it is the internet gateway route that makes that subnet public.
> - B: A network ACL filters traffic; without a route to an internet gateway, no internet traffic arrives.
> - C: A virtual private gateway is the AWS side of a Site-to-Site VPN, not an internet path.
>
> Review: [[3.5 Network Services]]

### Q32
A company's website ran in a single data center, and one power failure took it offline for a day. On AWS it now runs on instances in three Availability Zones behind a load balancer, so the site stays accessible if one Availability Zone fails. Which AWS Cloud benefit does this demonstrate?

- A. Elasticity
- B. Agility
- C. High availability
- D. Economies of scale

> [!success]- Answer
> **C.** High availability means a workload stays accessible despite failures, which multiple Availability Zones make straightforward.
> - A: Elasticity is adding and removing capacity as demand changes; the stem is about surviving a failure.
> - B: Agility is getting resources quickly to experiment and innovate.
> - D: Economies of scale explain AWS's lower prices.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q33
A healthcare company has signed the AWS Business Associate Addendum (BAA). Its architects want to use a recently released AWS service to process patient data. How should they confirm whether that service can be used for this purpose?

- A. Assume the service is covered, because AWS's infrastructure meets the compliance program
- B. Check the AWS Services in Scope by Compliance Program page for HIPAA-eligible services
- C. Run AWS Trusted Advisor checks against the service
- D. Enable AWS Security Hub in the account

> [!success]- Answer
> **B.** Compliance coverage varies by service, and AWS lists which services are in scope for each compliance program, including HIPAA-eligible services.
> - A: Not every service is in scope for every program, so coverage must be checked for each service.
> - C: Trusted Advisor checks the account against best practices; it does not state compliance program eligibility.
> - D: Security Hub checks resources against security standards; it does not say which services a program covers.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q34
A research lab runs tens of thousands of genomics jobs, each taking several hours. It wants AWS to queue the jobs and provision the right amount and type of compute for them automatically, without installing or managing batch scheduling software. Which service should it use?

- A. AWS Batch
- B. AWS Lambda
- C. AWS Step Functions
- D. Amazon Lightsail

> [!success]- Answer
> **A.** AWS Batch runs batch computing workloads, queuing jobs and provisioning compute dynamically based on their requirements.
> - B: A Lambda invocation can run for at most 15 minutes, far shorter than these jobs.
> - C: Step Functions orchestrates the steps of a workflow; it does not provision compute for job queues.
> - D: Lightsail provides simple virtual servers for small projects.
>
> Review: [[3.3 Compute Services]]

### Q35
Finance wants billing reports to show which IAM user or role created each resource, such as EC2 instances and S3 buckets, without asking engineers to add any tags. What should the management account do?

- A. Create a user-defined CreatedBy tag and require engineers to apply it
- B. Turn on AWS Config in every account
- C. Activate the AWS-generated aws:createdBy cost allocation tag in the Billing and Cost Management console
- D. Ask AWS Support to add creator details to the invoice

> [!success]- Answer
> **C.** AWS-generated cost allocation tags are applied by AWS. Once the management account activates aws:createdBy, AWS tags supported resources created after activation with the identity that created them, and the tag appears in billing reports.
> - A: A user-defined tag depends on engineers applying it, which the stem rules out.
> - B: Config records resource configurations; it does not add creator details to billing reports.
> - D: AWS Support does not customize invoices; cost allocation tags provide this.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q36
Which TWO methods give people temporary AWS credentials instead of long-term credentials? (Select TWO.)

- A. Creating IAM users with access keys that are rotated every 90 days
- B. Letting users in another AWS account assume a cross-account IAM role
- C. Sharing the root user credentials, protected by MFA
- D. Storing an IAM user's access keys in AWS Secrets Manager
- E. Having employees sign in through IAM Identity Center federated with the corporate identity provider

> [!success]- Answer
> **B and E.** Assuming a role and signing in through federation both issue temporary security credentials that expire automatically.
> - A: Access keys are long-term credentials, even when rotated.
> - C: Root credentials are long-term and must never be shared.
> - D: Storing access keys securely does not make them temporary.
>
> Review: [[2.3 Access Management and IAM]]

### Q37
A team regularly benchmarks new instance types and storage options to find the best performance for its workload. It serves users worldwide through Amazon CloudFront so they get low latency without the team building infrastructure in each country. Which Well-Architected Framework pillar do these practices represent?

- A. Reliability
- B. Cost optimization
- C. Sustainability
- D. Performance efficiency

> [!success]- Answer
> **D.** Experimenting more often and going global in minutes are Performance efficiency design principles.
> - A: Reliability focuses on recovering from failure and performing consistently.
> - B: Cost optimization focuses on the lowest price for the business value; the goal here is performance and latency.
> - C: Sustainability focuses on reducing environmental impact.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q38
A machine learning team needs a shared, high-performance file system for a cluster of compute instances during training. It must deliver very high throughput with sub-millisecond latency, present objects in an Amazon S3 bucket as files, and write results back to S3. Which service should it use?

- A. Amazon Elastic File System (Amazon EFS)
- B. Amazon FSx for Lustre
- C. Amazon FSx for Windows File Server
- D. S3 Glacier Instant Retrieval

> [!success]- Answer
> **B.** FSx for Lustre is a high-performance file system for HPC and ML workloads, and it can link to an S3 bucket, presenting objects as files and writing changes back.
> - A: EFS is a general-purpose shared file system for Linux; it does not link to an S3 bucket and present its objects as files.
> - C: FSx for Windows File Server provides SMB file shares for Windows applications.
> - D: Glacier Instant Retrieval is an S3 storage class for rarely accessed data, not a file system.
>
> Review: [[3.6 Storage Services]]

### Q39
A regulator requires a company to generate and store its encryption keys in dedicated, single-tenant hardware security modules (HSMs) that the company alone controls. Which service meets this requirement?

- A. AWS CloudHSM
- B. AWS Key Management Service (AWS KMS) with AWS managed keys
- C. AWS Secrets Manager
- D. AWS Certificate Manager (ACM)

> [!success]- Answer
> **A.** CloudHSM provides dedicated HSMs in your VPC that only you control.
> - B: KMS is a managed, multi-tenant service in which AWS operates the HSMs, and AWS managed keys are managed by AWS on the customer's behalf.
> - C: Secrets Manager stores and rotates secrets such as passwords; it does not provide HSMs.
> - D: ACM issues and manages SSL/TLS certificates.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q40
An engineer needs to check, just once, which Region a particular S3 bucket was created in. Which approach takes the least effort?

- A. Write an AWS CloudFormation template that describes the bucket
- B. Build a pipeline in AWS CodePipeline that reports bucket settings
- C. Look up the bucket in the AWS Management Console
- D. Write a Python program with the AWS SDK that queries the bucket

> [!success]- Answer
> **C.** For a one-time lookup, the console's web interface is the quickest option.
> - A: Infrastructure as code suits repeatable provisioning, not a single lookup.
> - B: A release pipeline is for repeatable software delivery.
> - D: Writing code is more effort than a one-time check needs; programmatic access suits automated or repeated tasks.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q41
A company brings its own Microsoft SQL Server and Oracle licenses to AWS (BYOL). It must track license usage across AWS and its on-premises servers and set rules that prevent it from using more licenses than it owns. Which service should it use?

- A. AWS Artifact
- B. AWS Marketplace
- C. AWS Trusted Advisor
- D. AWS License Manager

> [!success]- Answer
> **D.** License Manager centrally manages software licenses across AWS and on-premises environments and can enforce license limits.
> - A: Artifact provides compliance documents, not license tracking.
> - B: Marketplace sells third-party software; it does not track licenses the company already owns.
> - C: Trusted Advisor checks best practices; it does not enforce license rules.
>
> Review: [[1.4 Cloud Economics]]

### Q42
A security engineer wants to keep up with posts written by AWS experts that announce new security features and walk through security best practices and solutions. Which AWS resource should she follow?

- A. AWS Security Blog
- B. AWS Artifact
- C. AWS Trust and Safety team
- D. AWS Health Dashboard

> [!success]- Answer
> **A.** The AWS Security Blog publishes posts on new security features, best practices, and solutions.
> - B: Artifact provides compliance reports and agreements.
> - C: Trust and Safety handles reports of abuse of AWS resources.
> - D: The Health Dashboard reports service health and events affecting your account.
>
> Review: [[2.4 Security Components and Resources]]

### Q43
A large enterprise wants a team of experts employed by AWS to work alongside its own staff and deliver a data center migration project with defined outcomes. Which option should it engage?

- A. AWS Managed Services (AMS)
- B. AWS Professional Services
- C. AWS Marketplace
- D. AWS Trusted Advisor

> [!success]- Answer
> **B.** AWS Professional Services is AWS's own consulting organization, which works with customers to deliver projects such as migrations.
> - A: AMS operates a customer's AWS infrastructure on an ongoing basis; it is not a project consulting team.
> - C: Marketplace is a catalog of third-party software, data, and services.
> - D: Trusted Advisor is an automated best-practice checking tool.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q44
Developers want to create, publish, and secure REST APIs in front of AWS Lambda functions, with request throttling and API keys for partner access. Which service should they use?

- A. AWS AppSync
- B. Amazon CloudFront
- C. Amazon API Gateway
- D. AWS Global Accelerator

> [!success]- Answer
> **C.** API Gateway creates, publishes, secures, and monitors REST, HTTP, and WebSocket APIs, including throttling and API keys.
> - A: AppSync builds GraphQL and pub/sub APIs, not REST APIs.
> - B: CloudFront is a content delivery network; it does not create or manage APIs.
> - D: Global Accelerator improves availability and performance with static IP addresses; it does not manage APIs.
>
> Review: [[3.5 Network Services]]

### Q45
Which scenario is an example of elasticity?

- A. Developers launch a new test environment in minutes and delete it after the experiment.
- B. An application keeps serving users when one Availability Zone fails.
- C. AWS lowers its prices as its customer base grows.
- D. Instances are added automatically when a sales event starts and removed when it ends, so the company pays only for the capacity it uses.

> [!success]- Answer
> **D.** Elasticity is acquiring resources as demand rises and releasing them when it falls.
> - A: Fast, cheap experimentation is agility.
> - B: Surviving an Availability Zone failure is high availability.
> - C: Lower prices from aggregated usage are economies of scale.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q46
A company moves a containerized application from Amazon ECS running on EC2 instances to Amazon ECS on AWS Fargate. Which TWO tasks does the company no longer perform? (Select TWO.)

- A. Patching the operating system of the hosts that run the containers
- B. Choosing, scaling, and managing the EC2 instances in the cluster
- C. Securing the application code and container images
- D. Granting least-privilege IAM permissions to the tasks
- E. Configuring security groups for the tasks

> [!success]- Answer
> **A and B.** With Fargate, AWS provides and manages the underlying compute, including its operating system and capacity.
> - C: The customer remains responsible for its code and images.
> - D: IAM permissions are always the customer's responsibility.
> - E: Network access configuration, including security groups, stays with the customer.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q47
A company wants to be able to recover its on-premises application servers in AWS within minutes if its data center fails. It wants continuous block-level replication to a low-cost staging area in AWS, paying for full compute only during a recovery or a drill. It is not planning a migration. Which service should it use?

- A. AWS Elastic Disaster Recovery
- B. AWS Backup
- C. AWS Application Migration Service
- D. AWS Storage Gateway

> [!success]- Answer
> **A.** Elastic Disaster Recovery continuously replicates servers to a low-cost staging area in AWS and launches recovery instances within minutes when needed.
> - B: AWS Backup takes scheduled backups; restoring whole servers from them is slower and is not continuous replication.
> - C: Application Migration Service uses similar replication, but its purpose is a one-time move to AWS, and the company is not migrating.
> - D: Storage Gateway gives on-premises applications access to cloud storage; it does not recover servers in AWS.
>
> Review: [[3.6 Storage Services]]

### Q48
Security requires that every IAM user's password be at least 14 characters, include a symbol, and expire every 90 days. Where should the administrator enforce this?

- A. Automatic rotation in AWS Secrets Manager
- B. The IAM account password policy
- C. A service control policy (SCP) in AWS Organizations
- D. An AWS Config rule

> [!success]- Answer
> **B.** The IAM account password policy sets length, complexity, and expiration requirements for IAM user passwords.
> - A: Secrets Manager rotates application secrets, not IAM user sign-in passwords.
> - C: SCPs limit the maximum permissions available in accounts; they do not set password rules.
> - D: A Config rule can report whether the password policy meets requirements, but it does not enforce the rules on users.
>
> Review: [[2.3 Access Management and IAM]]

### Q49
A company has 600 EC2 instances and 200 on-premises servers. Administrators sign in to each server to apply patches and configuration changes, which takes days and leaves servers configured inconsistently. Which service automates patching and configuration across both environments?

- A. AWS CloudFormation
- B. AWS Config
- C. AWS Systems Manager
- D. AWS Trusted Advisor

> [!success]- Answer
> **C.** Systems Manager automates operational tasks such as patching and configuration on EC2 instances and on-premises servers, reducing manual labor and configuration drift.
> - A: CloudFormation provisions AWS resources from templates; it does not patch on-premises servers.
> - B: Config records and evaluates resource configurations; it does not apply patches.
> - D: Trusted Advisor makes best-practice recommendations; it changes nothing.
>
> Review: [[1.4 Cloud Economics]]

### Q50
An operations team wants to ingest application logs, run full-text searches across them, and build interactive dashboards for log analytics, using a managed service based on an open-source search and analytics engine. Which service should it use?

- A. Amazon Redshift
- B. Amazon Kendra
- C. Amazon Athena
- D. Amazon OpenSearch Service

> [!success]- Answer
> **D.** OpenSearch Service runs managed OpenSearch clusters for log analytics, full-text search, and dashboards.
> - A: Redshift is a data warehouse for analytical SQL queries.
> - B: Kendra is an intelligent search service that answers natural language questions from an organization's documents, not a log analytics engine.
> - C: Athena runs SQL queries on data in S3; it is not an open-source search engine with log dashboards.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q51
A company is considering moving objects from S3 Standard to S3 Standard-IA. Which TWO charges can apply in S3 Standard-IA but do not apply in S3 Standard? (Select TWO.)

- A. A per-GB monthly storage charge
- B. Per-request charges for GET and PUT requests
- C. A per-GB data retrieval fee
- D. A minimum storage duration charge of 30 days for objects deleted earlier
- E. A charge for data transferred in from the internet

> [!success]- Answer
> **C and D.** Standard-IA trades a lower storage price for a per-GB retrieval fee and a 30-day minimum storage duration.
> - A: Both classes charge for storage per GB.
> - B: Both classes charge per request.
> - E: Data transferred in from the internet is free for both.
>
> Review: [[4.1 AWS Pricing Models]]

### Q52
An auditor asks for a list of every IAM user in an account showing whether each has a password, when it was last used, whether MFA is enabled, and the status of each access key. Which feature provides this?

- A. IAM credential report
- B. AWS CloudTrail event history
- C. AWS Artifact
- D. Amazon Inspector

> [!success]- Answer
> **A.** The IAM credential report lists all users and the status of their credentials, including passwords, MFA, and access keys.
> - B: CloudTrail event history lists API calls, not the current status of each user's credentials.
> - C: Artifact provides AWS's compliance reports, not reports on the customer's users.
> - D: Inspector scans workloads for software vulnerabilities.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q53
A mining company has sensors on equipment at remote sites with intermittent connectivity. It wants gateway devices at each site to run machine learning inference and process data locally, keep working while offline, sync with the cloud when the connection returns, and receive software updates deployed from AWS. Which service should it use?

- A. AWS IoT Core
- B. AWS IoT Greengrass
- C. AWS Outposts
- D. AWS Wavelength

> [!success]- Answer
> **B.** IoT Greengrass is an edge runtime for building, deploying, and managing software on devices, which can process data and run inference locally even when disconnected.
> - A: IoT Core connects devices to the cloud and routes their messages; processing happens in the cloud, which needs connectivity.
> - C: Outposts installs AWS racks in a data center and needs a connection to its Region; it does not run on small gateway devices.
> - D: Wavelength places compute in 5G carrier networks for mobile applications.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q54
According to the AWS Cloud Adoption Framework (AWS CAF), which TWO are business outcomes that cloud transformation helps improve? (Select TWO.)

- A. Reduced business risk
- B. Guaranteed 100% application uptime
- C. Higher capital expenditure on hardware
- D. Removal of the need for application testing
- E. Improved environmental, social, and governance (ESG) performance

> [!success]- Answer
> **A and E.** AWS CAF names reduced business risk, improved ESG performance, increased revenue, and increased operational efficiency as outcomes.
> - B: No framework or service guarantees 100% uptime.
> - C: Cloud adoption shifts spending away from capital expenditure.
> - D: Applications still need testing in the cloud.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q55
Whether a company uses Amazon EC2, Amazon RDS, or AWS Lambda, which responsibility always stays with the company?

- A. Patching the database engine
- B. Managing the guest operating system
- C. Classifying its data and controlling who can access it
- D. Maintaining the virtualization layer

> [!success]- Answer
> **C.** Customer data and identity and access management are the customer's responsibility for every service.
> - A: AWS patches the database engine for RDS; it is the customer's job only when the database runs on EC2.
> - B: The customer manages the guest OS on EC2, but AWS manages it for RDS and Lambda.
> - D: The virtualization layer is always AWS's responsibility.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q56
A web application must send requests for /api/* to one group of instances and requests for /images/* to another group, based on the URL path. Which service should it use?

- A. Network Load Balancer
- B. Gateway Load Balancer
- C. Amazon Route 53 weighted routing
- D. Application Load Balancer

> [!success]- Answer
> **D.** Application Load Balancers work at the HTTP(S) layer and can route requests to different target groups based on URL path.
> - A: Network Load Balancers work at the transport layer (TCP and UDP) and do not inspect URL paths.
> - B: Gateway Load Balancers distribute traffic to virtual appliances such as firewalls.
> - C: Route 53 resolves domain names; it never sees the URL path of a request.
>
> Review: [[3.3 Compute Services]]

### Q57
A team uses automated tools so that people never need direct access to production data, applies controls at every layer (edge, VPC, subnet, instance, and application), and runs simulations to rehearse its response to security incidents. Which Well-Architected Framework pillar do these practices represent?

- A. Security
- B. Operational excellence
- C. Reliability
- D. Performance efficiency

> [!success]- Answer
> **A.** Keeping people away from data, applying security at all layers, and preparing for security events are Security pillar design principles.
> - B: Operational excellence also runs exercises, but its focus is operational procedures and changes, not protecting data and responding to security events.
> - C: Reliability focuses on recovering from failure and consistent performance.
> - D: Performance efficiency focuses on using resources efficiently.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q58
A company needs a connection from its data center to AWS that provides consistent network performance and does not travel over the public internet. Its security policy also requires that the traffic be encrypted with IPsec. Which TWO should it use together? (Select TWO.)

- A. AWS Global Accelerator
- B. AWS Direct Connect
- C. AWS Site-to-Site VPN
- D. An internet gateway with public IP addresses
- E. Amazon CloudFront

> [!success]- Answer
> **B and C.** Direct Connect provides the private, dedicated connection with consistent performance, and running a Site-to-Site VPN over it adds IPsec encryption.
> - A: Global Accelerator routes internet users to applications over the AWS network; it does not connect a data center privately.
> - D: An internet gateway sends traffic over the public internet.
> - E: CloudFront delivers content to end users.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q59
A security team wants one policy that grants exactly the permissions its own environment needs. The policy must be attached to five IAM groups and updated in one place when requirements change. Which type of policy should it use?

- A. An AWS managed policy
- B. A customer managed policy
- C. An inline policy embedded in each group
- D. A service control policy (SCP) attached to each group

> [!success]- Answer
> **B.** A customer managed policy is a standalone policy you write and maintain, which can be attached to many identities and edited once.
> - A: AWS managed policies are written and updated by AWS, cannot be edited, and are not tailored to one company's environment.
> - C: Inline policies are embedded in a single identity, so five groups would need five copies to update separately.
> - D: SCPs attach to accounts and organizational units, not IAM groups, and they limit permissions rather than grant them.
>
> Review: [[2.3 Access Management and IAM]]

### Q60
A company wants to see AWS events that affect its own resources, such as scheduled maintenance that will require an EC2 instance reboot, along with guidance on what action to take. Which service provides this?

- A. Amazon CloudWatch
- B. AWS Trusted Advisor
- C. AWS Health Dashboard
- D. AWS CloudTrail

> [!success]- Answer
> **C.** The AWS Health Dashboard shows AWS events affecting your account and resources, including scheduled changes, with remediation guidance. The AWS Health API provides the same information programmatically.
> - A: CloudWatch monitors your metrics and logs; it does not announce AWS maintenance events.
> - B: Trusted Advisor checks your configuration against best practices.
> - D: CloudTrail records API calls made in your account.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q61
A company lacks the staff to operate its AWS infrastructure. It wants AWS to handle day-to-day operations, including patching, monitoring, backups, incident management, and change management, following ITIL practices. Which option should it choose?

- A. AWS Enterprise Support
- B. AWS Professional Services
- C. AWS Systems Manager
- D. AWS Managed Services (AMS)

> [!success]- Answer
> **D.** AMS provides ongoing operational management of a customer's AWS infrastructure.
> - A: Enterprise Support gives guidance and case support; the customer's staff still run the infrastructure.
> - B: Professional Services delivers projects; it does not take over day-to-day operations.
> - C: Systems Manager is a tool that automates operations, but the company would still need staff to use it.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q62
During cloud adoption, a company's architects and engineers focus on building an enterprise-grade cloud platform: designing the architecture, automating provisioning and orchestration, and setting up CI/CD for modern application development. Which AWS CAF perspective covers this work?

- A. Platform
- B. Operations
- C. Governance
- D. Business

> [!success]- Answer
> **A.** The Platform perspective covers platform architecture and engineering, provisioning and orchestration, modern application development, and CI/CD.
> - B: Operations covers running the platform day to day: observability, incident management, and patching.
> - C: Governance covers program management, risk, and cloud financial management.
> - D: Business covers strategy, product management, and business outcomes.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q63
A company wants to automatically and continuously scan its EC2 instances, container images in Amazon ECR, and Lambda functions for known software vulnerabilities and unintended network exposure. Which service should it use?

- A. Amazon GuardDuty
- B. Amazon Inspector
- C. Amazon Macie
- D. Amazon Detective

> [!success]- Answer
> **B.** Inspector continuously scans EC2, ECR images, and Lambda functions for software vulnerabilities and unintended network exposure.
> - A: GuardDuty detects active threats from logs, such as unusual API calls; it does not scan software for vulnerabilities.
> - C: Macie discovers sensitive data in S3.
> - D: Detective investigates the root cause of security findings.
>
> Review: [[2.4 Security Components and Resources]]

### Q64
Which TWO factors can differ between AWS Regions and should be considered when choosing a Region for a workload? (Select TWO.)

- A. The Region the AWS account was created in, because accounts can use only one Region
- B. Support plan response times, which differ by Region
- C. S3 durability, which is higher in Regions with more edge locations
- D. Whether the services and features the workload needs are available in that Region
- E. Prices for the same service

> [!success]- Answer
> **D and E.** Not every service or feature is available in every Region, and prices for the same service vary between Regions.
> - A: An account can use resources in many Regions.
> - B: Support plan response times are the same regardless of Region.
> - C: S3 durability does not depend on edge locations or Region.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q65
A company launches EC2 instances from an AWS-provided Microsoft Windows Server Amazon Machine Image (AMI). It owns no Windows Server licenses. How is the Windows Server license paid for?

- A. The company must buy licenses from Microsoft and register them in AWS License Manager.
- B. The company must run the instances on Dedicated Hosts.
- C. The license cost is included in the instance's hourly price.
- D. Windows Server licenses are free on AWS.

> [!success]- Answer
> **C.** AWS-provided Windows AMIs use the license-included model: the Windows Server license is built into the instance price.
> - A: That describes BYOL, which needs licenses the company does not have.
> - B: Dedicated Hosts are needed only for some BYOL scenarios, not for license-included instances.
> - D: The license is not free; it is part of a higher hourly rate than the equivalent Linux instance.
>
> Review: [[1.4 Cloud Economics]]

---

## Scoring table

Mark each question 1 (correct) or 0 (wrong). Select TWO questions score 1 only if both choices are right.

| Q | Domain | Task statement | Answer | Score |
|---|---|---|---|---|
| 1 | 3 | 3.3 Compute | C | |
| 2 | 2 | 2.2 Security, governance, compliance | B | |
| 3 | 1 | 1.1 Benefits | A | |
| 4 | 3 | 3.8 Other in-scope services | D | |
| 5 | 2 | 2.1 Shared responsibility | B | |
| 6 | 4 | 4.1 Pricing models | A | |
| 7 | 1 | 1.2 Well-Architected | C | |
| 8 | 3 | 3.4 Database | D | |
| 9 | 2 | 2.4 Security components | A | |
| 10 | 3 | 3.2 Global infrastructure | B | |
| 11 | 1 | 1.4 Cloud economics | A, C | |
| 12 | 2 | 2.3 Access management | C | |
| 13 | 4 | 4.2 Billing and cost management | D | |
| 14 | 3 | 3.5 Network | B | |
| 15 | 2 | 2.2 Security, governance, compliance | B, D | |
| 16 | 1 | 1.3 Migration and CAF | C | |
| 17 | 3 | 3.6 Storage | A | |
| 18 | 2 | 2.3 Access management | D | |
| 19 | 3 | 3.1 Deploying and operating | B | |
| 20 | 1 | 1.2 Well-Architected | C, E | |
| 21 | 4 | 4.3 Support and resources | A | |
| 22 | 2 | 2.1 Shared responsibility | C | |
| 23 | 3 | 3.4 Database | D | |
| 24 | 1 | 1.4 Cloud economics | B | |
| 25 | 2 | 2.4 Security components | A | |
| 26 | 3 | 3.2 Global infrastructure | C | |
| 27 | 1 | 1.3 Migration and CAF | D | |
| 28 | 4 | 4.1 Pricing models | B | |
| 29 | 3 | 3.7 AI/ML and analytics | A, D | |
| 30 | 2 | 2.1 Shared responsibility | A | |
| 31 | 3 | 3.5 Network | D | |
| 32 | 1 | 1.1 Benefits | C | |
| 33 | 2 | 2.2 Security, governance, compliance | B | |
| 34 | 3 | 3.3 Compute | A | |
| 35 | 4 | 4.2 Billing and cost management | C | |
| 36 | 2 | 2.3 Access management | B, E | |
| 37 | 1 | 1.2 Well-Architected | D | |
| 38 | 3 | 3.6 Storage | B | |
| 39 | 2 | 2.2 Security, governance, compliance | A | |
| 40 | 3 | 3.1 Deploying and operating | C | |
| 41 | 1 | 1.4 Cloud economics | D | |
| 42 | 2 | 2.4 Security components | A | |
| 43 | 4 | 4.3 Support and resources | B | |
| 44 | 3 | 3.5 Network | C | |
| 45 | 1 | 1.1 Benefits | D | |
| 46 | 2 | 2.1 Shared responsibility | A, B | |
| 47 | 3 | 3.6 Storage | A | |
| 48 | 2 | 2.3 Access management | B | |
| 49 | 1 | 1.4 Cloud economics | C | |
| 50 | 3 | 3.7 AI/ML and analytics | D | |
| 51 | 4 | 4.1 Pricing models | C, D | |
| 52 | 2 | 2.2 Security, governance, compliance | A | |
| 53 | 3 | 3.8 Other in-scope services | B | |
| 54 | 1 | 1.3 Migration and CAF | A, E | |
| 55 | 2 | 2.1 Shared responsibility | C | |
| 56 | 3 | 3.3 Compute | D | |
| 57 | 1 | 1.2 Well-Architected | A | |
| 58 | 3 | 3.1 Deploying and operating | B, C | |
| 59 | 2 | 2.3 Access management | B | |
| 60 | 4 | 4.3 Support and resources | C | |
| 61 | 3 | 3.8 Other in-scope services | D | |
| 62 | 1 | 1.3 Migration and CAF | A | |
| 63 | 2 | 2.4 Security components | B | |
| 64 | 3 | 3.2 Global infrastructure | D, E | |
| 65 | 1 | 1.4 Cloud economics | C | |

### Totals by domain

| Domain | Questions | Your score | Percent | Target (90%) |
|---|---|---|---|---|
| 1 Cloud Concepts | 3, 7, 11, 16, 20, 24, 27, 32, 37, 41, 45, 49, 54, 57, 62, 65 | /16 | | 15 |
| 2 Security and Compliance | 2, 5, 9, 12, 15, 18, 22, 25, 30, 33, 36, 39, 42, 46, 48, 52, 55, 59, 63 | /19 | | 17 |
| 3 Cloud Technology and Services | 1, 4, 8, 10, 14, 17, 19, 23, 26, 29, 31, 34, 38, 40, 44, 47, 50, 53, 56, 58, 61, 64 | /22 | | 20 |
| 4 Billing, Pricing, and Support | 6, 13, 21, 28, 35, 43, 51, 60 | /8 | | 7 |
| **Total** | 65 | /65 | | 59 |

Questions per task statement: 1.1 ×3, 1.2 ×4, 1.3 ×4, 1.4 ×5; 2.1 ×5, 2.2 ×5, 2.3 ×5, 2.4 ×4; 3.1 ×3, 3.2 ×3, 3.3 ×3, 3.4 ×2, 3.5 ×3, 3.6 ×3, 3.7 ×2, 3.8 ×3; 4.1 ×3, 4.2 ×2, 4.3 ×3.

Any domain below 80%: reread that domain's task notes, then drill the matching flashcard deck and practice set ([[Practice - Domain 1]], [[Practice - Domain 2]], [[Practice - Domain 3 (Part 1)]], [[Practice - Domain 3 (Part 2)]], [[Practice - Domain 4]]). For look-alike misses, use [[Commonly Confused Services]]. Compare your result with [[Mock Exam 1]]: a domain weak on both exams needs the most review time.
