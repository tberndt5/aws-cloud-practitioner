---
tags:
  - clf-c02
  - practice
  - mock-exam
---
# Mock Exam 1

> [!info] Instructions
> - **65 questions, 90 minutes, closed book.** Set a timer and do not open the answers until you finish all 65.
> - The real exam scores 50 questions and includes 15 unscored ones you cannot identify, reported as a scaled score of 100–1,000. **700 passes**, roughly 70% correct. Your target here is **90% (59 of 65)**.
> - There is no penalty for guessing. Never leave a question blank.
> - "Select TWO" questions need both correct answers to score. There are 11 of them.
> - Domain weighting matches the exam guide: Domain 1 = 16 questions, Domain 2 = 19, Domain 3 = 22, Domain 4 = 8, interleaved as on the real exam.
> - When you finish, mark each answer right or wrong in the [[#Scoring table]] and total each domain. Reread the task note linked in each Review line for every miss.

> [!note] Support plan names
> This exam uses the support plans in the CLF-C02 exam guide (Basic, Developer, Business, Enterprise On-Ramp, Enterprise). Current status: AWS stopped selling Developer and Business Support to new subscribers on December 2, 2025, and those plans and Enterprise On-Ramp end on January 1, 2027 (replaced by Business Support+, Enterprise, and Unified Operations). The exam still tests the older names.

---

### Q1
A company runs a data warehousing workload on Amazon EC2. The workload needs high, sequential read and write access to very large data sets on local storage. Which EC2 instance category is the best fit?

- A. Compute optimized
- B. Memory optimized
- C. Storage optimized
- D. Accelerated computing

> [!success]- Answer
> **C.** Storage optimized instances are designed for high, sequential read and write access to very large data sets on local storage, such as data warehousing and distributed file systems.
> - A: Compute optimized suits CPU-bound work such as batch processing, media transcoding, and game servers.
> - B: Memory optimized suits workloads that hold large data sets in memory, such as in-memory caches and databases.
> - D: Accelerated computing uses GPUs or other hardware accelerators for ML training, graphics, and similar work.
>
> Review: [[3.3 Compute Services]]

### Q2
A healthcare company's compliance officer must review AWS's ISO 27001 certification and accept a Business Associate Addendum (BAA) before the company stores patient data on AWS. Where can the officer do both?

- A. AWS Artifact
- B. AWS Audit Manager
- C. AWS Security Hub
- D. AWS Trusted Advisor

> [!success]- Answer
> **A.** AWS Artifact is the self-service portal for AWS's compliance reports and certifications and for agreements such as the BAA.
> - B: Audit Manager collects evidence about the customer's own AWS usage; it does not hold AWS's certifications or agreements.
> - C: Security Hub aggregates security findings and runs best-practice checks on the customer's resources.
> - D: Trusted Advisor checks the customer's account against best practices.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q3
A retailer buys enough servers to handle its holiday-season peak. For the other ten months, most of those servers sit idle. Which AWS Cloud benefit most directly solves this problem?

- A. Economies of scale
- B. Elasticity
- C. Global reach
- D. High availability

> [!success]- Answer
> **B.** Elasticity lets the retailer add capacity for the peak and remove it afterward, paying only for what it uses, so it no longer has to buy for the peak.
> - A: Economies of scale lower AWS's per-unit prices but do not address idle capacity.
> - C: Global reach is about deploying in many geographic locations.
> - D: High availability is about keeping a workload running despite failures.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q4
An e-commerce web tier sends orders directly to an order-processing service. During flash sales, the processing service is overwhelmed and orders are lost. The company wants orders to be stored durably until the processing service is ready to handle them. Which service should it add between the two tiers?

- A. Amazon Simple Notification Service (Amazon SNS)
- B. Amazon EventBridge
- C. AWS Step Functions
- D. Amazon Simple Queue Service (Amazon SQS)

> [!success]- Answer
> **D.** SQS is a message queue that buffers messages until consumers pull them, which decouples the tiers and absorbs spikes.
> - A: SNS pushes messages to subscribers immediately; it does not hold them until a slow consumer is ready.
> - B: EventBridge routes events to targets by rule; it is not a buffer for a consumer that falls behind.
> - C: Step Functions orchestrates the steps of a workflow; it does not queue a backlog of incoming orders.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q5
A company builds an application on AWS Lambda. Under the AWS shared responsibility model, which task is the company's responsibility?

- A. Patching the operating system of the servers that run the functions
- B. Adding servers as the number of invocations grows
- C. Writing secure function code and limiting the permissions of the function's execution role
- D. Physical security of the data centers that host Lambda

> [!success]- Answer
> **C.** With Lambda, the customer remains responsible for its code, its data, and the IAM permissions it grants.
> - A: AWS patches the operating system that Lambda runs on.
> - B: Lambda scales automatically; AWS manages the underlying capacity.
> - D: Physical security is always AWS's responsibility.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q6
A startup wants an email when its forecasted AWS spend for the month is expected to exceed $2,000, and another when actual spend passes $1,500. Which service should it use?

- A. AWS Cost Explorer
- B. AWS Budgets
- C. AWS Pricing Calculator
- D. AWS Cost and Usage Report

> [!success]- Answer
> **B.** AWS Budgets sets cost thresholds and sends alerts on actual or forecasted spend.
> - A: Cost Explorer visualizes and forecasts spend but is not the tool for threshold alerts.
> - C: Pricing Calculator estimates the cost of a planned architecture; it does not track actual spend.
> - D: The Cost and Usage Report is a detailed data file delivered to S3; it sends no alerts.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q7
An architecture team adopts these design principles: automatically recover from failure, scale horizontally to increase aggregate workload availability, and stop guessing capacity. Which pillar of the AWS Well-Architected Framework do these principles belong to?

- A. Performance efficiency
- B. Operational excellence
- C. Cost optimization
- D. Reliability

> [!success]- Answer
> **D.** All three are design principles of the Reliability pillar, which covers a workload performing its function correctly and consistently and recovering from failure.
> - A: Performance efficiency principles include democratizing advanced technologies, going global in minutes, and using serverless architectures.
> - B: Operational excellence principles include performing operations as code and making frequent, small, reversible changes.
> - C: Cost optimization principles include adopting a consumption model and measuring overall efficiency.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q8
A company wants to migrate an on-premises Oracle database to Amazon Aurora PostgreSQL while the source database continues to serve users during the migration. Which TWO AWS services should it use? (Select TWO.)

- A. AWS Application Migration Service
- B. AWS Database Migration Service (AWS DMS)
- C. AWS Schema Conversion Tool (AWS SCT)
- D. AWS Application Discovery Service
- E. AWS Migration Hub

> [!success]- Answer
> **B and C.** AWS SCT converts the Oracle schema and code to PostgreSQL (a heterogeneous migration), and AWS DMS moves the data with continuous replication so the source stays online.
> - A: Application Migration Service rehosts whole servers onto EC2; it does not convert a database to a different engine.
> - D: Application Discovery Service inventories on-premises servers to plan a migration; it moves no data.
> - E: Migration Hub tracks migration progress; it does not perform the migration.
>
> Review: [[3.4 Database Services]]

### Q9
A security team must block all traffic from a specific range of malicious IP addresses to every instance in a subnet, even where an instance's security group allows that traffic. What should the team use?

- A. A network ACL rule that denies the IP range
- B. A security group rule that denies the IP range
- C. AWS Shield Standard
- D. Amazon GuardDuty

> [!success]- Answer
> **A.** Network ACLs operate at the subnet level and support explicit deny rules, and they are evaluated before traffic reaches the instance's security group.
> - B: Security groups support allow rules only; you cannot write a deny rule.
> - C: Shield Standard provides automatic DDoS protection; it does not block a chosen IP range.
> - D: GuardDuty detects threats and creates findings; it does not block traffic itself.
>
> Review: [[2.4 Security Components and Resources]]

### Q10
Which statement correctly describes an AWS Availability Zone?

- A. A caching site that Amazon CloudFront uses to deliver content to nearby users
- B. A single data center shared by two neighboring Regions so that either can fail over to it
- C. A deployment of AWS infrastructure inside a telecommunications provider's 5G network
- D. One or more discrete data centers with redundant power, networking, and connectivity, isolated from failures in other Availability Zones in the same Region

> [!success]- Answer
> **D.** An Availability Zone is one or more discrete data centers within a Region, built so that Availability Zones do not share single points of failure.
> - A: That describes an edge location.
> - B: Availability Zones belong to exactly one Region and are not shared between Regions.
> - C: That describes an AWS Wavelength Zone.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q11
Which change is an example of trading fixed expense for variable expense?

- A. Buying new servers every five years and depreciating them
- B. Signing a 10-year lease for colocation space
- C. Replacing owned servers with EC2 instances that are billed per second only while they run
- D. Prepaying a three-year hardware maintenance contract

> [!success]- Answer
> **C.** Paying per second only for compute that is running turns a fixed infrastructure cost into a variable cost that follows usage.
> - A: Buying and depreciating servers is a fixed capital expense.
> - B: A long-term lease is a fixed cost regardless of usage.
> - D: A prepaid maintenance contract is a fixed cost.
>
> Review: [[1.4 Cloud Economics]]

### Q12
Which TWO tasks can be performed only by signing in as the AWS account root user of a standalone account (one that is not part of AWS Organizations)? (Select TWO.)

- A. Close the AWS account
- B. Create an IAM user with administrator permissions
- C. Register as a seller in the Reserved Instance Marketplace
- D. Enable MFA for an IAM user
- E. Create an AWS Cost and Usage Report

> [!success]- Answer
> **A and C.** Closing a standalone account and registering as a seller in the Reserved Instance Marketplace are on AWS's list of tasks that require root user credentials.
> - B: An IAM user or role with IAM permissions can create other IAM users.
> - D: An IAM administrator, or the user themselves with permission, can enable MFA for an IAM user.
> - E: An IAM identity with billing permissions can create a Cost and Usage Report.
>
> Review: [[2.3 Access Management and IAM]]

### Q13
A company runs EC2 instances across several instance families in two Regions and is moving some workloads to AWS Fargate and AWS Lambda. It wants a 3-year commitment discount that automatically applies across all of this usage. Which option should it choose?

- A. Compute Savings Plans
- B. EC2 Instance Savings Plans
- C. Standard Reserved Instances
- D. Convertible Reserved Instances

> [!success]- Answer
> **A.** Compute Savings Plans apply to EC2 usage regardless of instance family, size, OS, or Region, and also to Fargate and Lambda.
> - B: EC2 Instance Savings Plans are tied to one instance family in one Region and do not cover Fargate or Lambda.
> - C: Standard Reserved Instances apply only to matching EC2 instance attributes and do not cover Fargate or Lambda.
> - D: Convertible Reserved Instances can be exchanged for other EC2 configurations but still do not cover Fargate or Lambda.
>
> Review: [[4.1 AWS Pricing Models]]

### Q14
A multiplayer game uses UDP. Players around the world connect to game servers in two AWS Regions. The company wants two static IP addresses that players' networks can allow-list, with traffic carried over the AWS global network to the nearest healthy Region. Which service meets these needs?

- A. Amazon CloudFront
- B. AWS Global Accelerator
- C. Amazon Route 53 latency-based routing
- D. AWS Direct Connect

> [!success]- Answer
> **B.** Global Accelerator provides static anycast IP addresses and routes TCP and UDP traffic over the AWS backbone to the closest healthy endpoint.
> - A: CloudFront is a content delivery network for caching HTTP(S) content and does not give you fixed static IP addresses for a UDP game.
> - C: Route 53 returns DNS answers; it does not provide static IP addresses or carry traffic over the AWS network.
> - D: Direct Connect is a private link from a customer's data center to AWS, not a path for public players.
>
> Review: [[3.5 Network Services]]

### Q15
An S3 bucket was deleted yesterday. The security team must identify which IAM principal made the request and the source IP address it came from. Which service provides this information?

- A. Amazon CloudWatch metrics
- B. AWS Config
- C. AWS X-Ray
- D. AWS CloudTrail

> [!success]- Answer
> **D.** CloudTrail records API calls, including the identity of the caller, the time, and the source IP address.
> - A: CloudWatch metrics measure performance and usage; they do not record who called an API.
> - B: Config records what resources' configurations were and how they changed; the caller identity and source IP come from CloudTrail.
> - C: X-Ray traces requests through an application for performance troubleshooting.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q16
During its cloud adoption, a company's leaders worry that staff lack cloud skills and that teams resist new ways of working. Which AWS Cloud Adoption Framework (AWS CAF) perspective focuses on culture, organizational structure, and workforce transformation?

- A. Governance
- B. People
- C. Operations
- D. Platform

> [!success]- Answer
> **B.** The People perspective covers culture, organizational design, leadership, and building cloud skills across the workforce.
> - A: Governance covers program and project management, benefits management, risk, and cloud financial management.
> - C: Operations covers running and supporting cloud services (monitoring, incident management, availability).
> - D: Platform covers building the cloud platform and architecture.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q17
Twelve Linux EC2 instances in three Availability Zones must read and write the same files at the same time through a standard file system interface. Storage must grow and shrink automatically as files are added and removed. Which service meets these requirements?

- A. Amazon Elastic File System (Amazon EFS)
- B. Amazon Elastic Block Store (Amazon EBS) volumes with Multi-Attach
- C. Amazon FSx for Windows File Server
- D. EC2 instance store

> [!success]- Answer
> **A.** EFS is a serverless NFS file system that many Linux instances across multiple Availability Zones can mount at once, and it scales automatically.
> - B: An EBS volume lives in one Availability Zone, and Multi-Attach is limited to instances in that same Availability Zone; EBS also does not grow automatically.
> - C: FSx for Windows File Server provides SMB file shares for Windows workloads.
> - D: Instance store is temporary block storage attached to one host and is not shared.
>
> Review: [[3.6 Storage Services]]

### Q18
A company has 30 AWS accounts in AWS Organizations. Employees should sign in once with their existing corporate identity provider and then access only the accounts and permissions assigned to them. Which service provides this?

- A. Amazon Cognito
- B. IAM users created in each account with the same password policy
- C. AWS IAM Identity Center (AWS Single Sign-On)
- D. AWS Directory Service

> [!success]- Answer
> **C.** IAM Identity Center provides workforce single sign-on across the accounts in an organization and can federate with an external identity provider.
> - A: Cognito handles sign-up and sign-in for customers of web and mobile applications, not workforce access to AWS accounts.
> - B: Separate IAM users in 30 accounts means many long-term credentials and no single sign-on.
> - D: Directory Service runs Microsoft Active Directory; by itself it does not assign access to multiple AWS accounts.
>
> Review: [[2.3 Access Management and IAM]]

### Q19
A developer is writing a Java application that, as part of its normal processing, uploads files to Amazon S3 and sends messages to Amazon SQS. What is the most appropriate way for the application to call these services?

- A. AWS Management Console
- B. AWS SDK for Java
- C. AWS CloudFormation
- D. AWS CloudShell

> [!success]- Answer
> **B.** The AWS SDKs let application code call AWS APIs in the developer's programming language.
> - A: The console is a web interface for people, not for application code.
> - C: CloudFormation provisions infrastructure from templates; it does not perform an application's runtime operations.
> - D: CloudShell is a browser-based shell for interactive commands, not a library an application uses.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q20
A company sets goals to reduce the energy consumed by its workloads. It plans to maximize utilization, use managed services, and choose Regions partly based on their environmental impact. Which Well-Architected Framework pillar guides these goals?

- A. Cost optimization
- B. Performance efficiency
- C. Operational excellence
- D. Sustainability

> [!success]- Answer
> **D.** The Sustainability pillar focuses on environmental impact, especially energy consumption and efficiency.
> - A: Cost optimization focuses on delivering business value at the lowest price; lower cost is not the stated goal here.
> - B: Performance efficiency focuses on using resources efficiently to meet performance requirements.
> - C: Operational excellence focuses on running and improving operations.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q21
Which TWO types of data transfer are typically free of charge on AWS? (Select TWO.)

- A. Data transferred into AWS from the internet
- B. Data transferred out from an EC2 instance to the internet
- C. Data transferred between two AWS Regions
- D. Data transferred between Amazon EC2 and Amazon S3 within the same Region
- E. Data transferred between EC2 instances in different Availability Zones

> [!success]- Answer
> **A and D.** Inbound data transfer from the internet is free, and data transferred directly between S3 and EC2 in the same Region is free.
> - B: Data transfer out to the internet is charged per GB.
> - C: Inter-Region data transfer is charged.
> - E: Data transfer between Availability Zones is charged.
>
> Review: [[4.1 AWS Pricing Models]]

### Q22
A company runs a web application on Amazon EC2 instances. Which TWO tasks are the company's responsibility under the shared responsibility model? (Select TWO.)

- A. Maintaining the hypervisor
- B. Patching the guest operating system
- C. Replacing failed physical disks in the host
- D. Securing AWS edge locations
- E. Configuring security group rules

> [!success]- Answer
> **B and E.** On EC2 (infrastructure as a service), the customer manages the guest OS, including patches, and the firewall configuration such as security groups.
> - A: AWS secures and maintains the hypervisor.
> - C: Hardware maintenance is AWS's responsibility.
> - D: Edge location management is AWS's responsibility.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q23
A gaming company needs a Redis-compatible database that serves leaderboard reads with microsecond latency and also stores the data durably as the primary database, without a separate database behind it. Which service fits best?

- A. Amazon DynamoDB
- B. Amazon MemoryDB for Redis
- C. Amazon Neptune
- D. Amazon Redshift

> [!success]- Answer
> **B.** MemoryDB for Redis is a durable, Redis-compatible, in-memory database that can serve as the primary database with microsecond reads.
> - A: DynamoDB is a key-value database with single-digit millisecond latency and is not Redis compatible.
> - C: Neptune is a graph database for highly connected data.
> - D: Redshift is a data warehouse for analytics, not a low-latency primary store.
>
> Review: [[3.4 Database Services]]

### Q24
Over three months, a company's EC2 instances averaged 6% CPU utilization and 15% memory utilization. Which action is an example of rightsizing?

- A. Purchasing 3-year Standard Reserved Instances for the current instances
- B. Moving the instances to a Region with lower prices
- C. Adding the instances to an Auto Scaling group with a minimum of four instances
- D. Changing to smaller instance types that match the measured utilization

> [!success]- Answer
> **D.** Rightsizing means matching instance type and size to actual workload needs, which here means smaller instances.
> - A: Buying Reserved Instances for oversized instances locks in the waste for three years.
> - B: Changing Regions changes the price, not the fit between instance size and workload.
> - C: A minimum of four instances adds capacity the workload does not need.
>
> Review: [[1.4 Cloud Economics]]

### Q25
A web application behind an Application Load Balancer is receiving requests that contain SQL injection and cross-site scripting attempts. Which service should inspect and block these HTTP requests?

- A. AWS WAF
- B. AWS Shield Standard
- C. Amazon GuardDuty
- D. Amazon Inspector

> [!success]- Answer
> **A.** AWS WAF filters HTTP(S) requests on resources such as Application Load Balancers, with rules that block SQL injection and cross-site scripting.
> - B: Shield Standard protects against network and transport layer DDoS attacks, not application-layer injection attempts.
> - C: GuardDuty detects threats from logs and creates findings; it does not block web requests.
> - D: Inspector scans workloads for software vulnerabilities; it does not filter traffic.
>
> Review: [[2.4 Security Components and Resources]]

### Q26
A company is building an augmented reality application for smartphones on 5G networks. It needs single-digit millisecond latency by running compute inside the telecommunications provider's network. Which AWS offering should it use?

- A. AWS Local Zones
- B. AWS Outposts
- C. AWS Wavelength
- D. Amazon CloudFront

> [!success]- Answer
> **C.** AWS Wavelength embeds AWS compute and storage in telecommunications providers' 5G networks for ultra-low latency to mobile devices.
> - A: Local Zones place AWS infrastructure in large metro areas, not inside the carrier's 5G network.
> - B: Outposts places AWS racks in the customer's own data center.
> - D: CloudFront caches content at edge locations; it does not run application compute inside a 5G network.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q27
A company must move 150 TB of archived video from its data center to Amazon S3 within three weeks, at the lowest cost. Its 100 Mbps internet connection is already heavily used. Which approach is most appropriate?

- A. AWS DataSync over the existing internet connection
- B. Ordering a new AWS Direct Connect connection
- C. AWS Snowball Edge devices
- D. AWS Transfer Family with SFTP

> [!success]- Answer
> **C.** Snowball Edge devices move data physically, so the transfer does not depend on the constrained network. At 100 Mbps, 150 TB would take more than four months even with the whole link.
> - A: DataSync transfers over the network, which is far too slow here.
> - B: A Direct Connect circuit typically takes weeks to provision and adds port and circuit costs for a one-time move.
> - D: Transfer Family is still limited by the same internet connection.
>
> Current status: AWS Snowball Edge closed to new customers on November 7, 2025. The exam still treats Snowball as the answer for large offline transfers.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q28
A company needs 24/7 phone access to Cloud Support Engineers, a response within 1 hour when a production system is down, and the full set of AWS Trusted Advisor checks. It wants the lowest-cost support plan that meets these needs. Which plan should it choose?

- A. Developer
- B. Business
- C. Enterprise On-Ramp
- D. Enterprise

> [!success]- Answer
> **B.** Business Support is the lowest plan with 24/7 phone, web, and chat access, a production-system-down response under 1 hour, and all Trusted Advisor checks.
> - A: Developer offers business-hours web access, core Trusted Advisor checks only, and no production-system-down response time.
> - C: Enterprise On-Ramp meets the needs but costs more than Business.
> - D: Enterprise meets the needs but is the most expensive plan.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q29
A retailer wants to analyze thousands of written product reviews to decide whether each is positive, negative, or neutral and to extract key phrases. It does not want to build machine learning models. Which service should it use?

- A. Amazon Comprehend
- B. Amazon Kendra
- C. Amazon Textract
- D. Amazon SageMaker

> [!success]- Answer
> **A.** Comprehend uses natural language processing to detect sentiment, key phrases, and entities in text without any model building.
> - B: Kendra is an intelligent search service for finding answers in documents.
> - C: Textract extracts text and data from scanned documents; it does not judge sentiment.
> - D: SageMaker is for building, training, and deploying your own models, which the company wants to avoid.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q30
A company uses Amazon RDS for MySQL. Which task is AWS responsible for?

- A. Creating database users and granting them privileges
- B. Configuring the security group that controls access to the database
- C. Deciding whether to encrypt the database at rest
- D. Patching the operating system of the database host

> [!success]- Answer
> **D.** With a managed service such as RDS, AWS patches the underlying operating system.
> - A: Database users and privileges are the customer's responsibility.
> - B: Network access configuration, including security groups, is the customer's responsibility.
> - C: Choosing to enable encryption is the customer's decision; AWS provides the capability.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q31
A company wants to register a domain name for its application and use DNS to automatically route users away from a Region whose endpoint fails a health check. Which service should it use?

- A. Amazon CloudFront
- B. Elastic Load Balancing
- C. Amazon Route 53
- D. AWS Global Accelerator

> [!success]- Answer
> **C.** Route 53 registers domains, answers DNS queries, and supports health checks with failover routing.
> - A: CloudFront is a content delivery network; it does not register domains.
> - B: Elastic Load Balancing distributes traffic across targets within a Region; it does not register domains or provide DNS failover between Regions.
> - D: Global Accelerator can fail over between Regions but works with static IP addresses, not DNS, and does not register domains.
>
> Review: [[3.5 Network Services]]

### Q32
Which TWO statements describe how customers benefit from AWS's economies of scale? (Select TWO.)

- A. Customers must sign a multi-year contract to receive AWS's lower prices.
- B. Because usage from hundreds of thousands of customers is aggregated, AWS achieves lower costs and passes them on as lower pay-as-you-go prices.
- C. Customers no longer pay for data transferred out to the internet.
- D. AWS has reduced its prices many times as it has grown.
- E. Every customer receives dedicated hardware at no extra cost.

> [!success]- Answer
> **B and D.** Aggregated usage lowers AWS's per-unit costs, and AWS has passed those savings on through many price reductions.
> - A: Pay-as-you-go prices require no contract.
> - C: Data transfer out to the internet is still charged.
> - E: Dedicated hardware (Dedicated Hosts and Instances) costs extra.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q33
A company must be able to show the configuration history of every security group over the past 90 days and be notified when any S3 bucket allows public read access. Which service meets both requirements?

- A. AWS CloudTrail
- B. AWS Config
- C. AWS Audit Manager
- D. AWS Trusted Advisor

> [!success]- Answer
> **B.** Config records resource configuration history and evaluates resources against rules, such as a rule that flags publicly readable buckets.
> - A: CloudTrail records the API calls that made changes, not a browsable history of each resource's configuration.
> - C: Audit Manager collects evidence for audits; it relies on sources such as Config.
> - D: Trusted Advisor can flag open bucket permissions but keeps no configuration history.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q34
A company runs long-running containerized services on Amazon ECS. The operations team no longer wants to patch, scale, or manage the EC2 instances in the cluster. What should the company use?

- A. AWS Fargate
- B. AWS Lambda
- C. Amazon EKS with self-managed nodes
- D. Amazon EC2 Auto Scaling

> [!success]- Answer
> **A.** Fargate is a serverless compute engine for ECS and EKS, so containers run without any EC2 instances to manage.
> - B: Lambda runs functions for at most 15 minutes per invocation, so it does not fit long-running services.
> - C: Self-managed nodes still require the team to manage EC2 instances.
> - D: EC2 Auto Scaling changes the number of instances but the team still manages them.
>
> Review: [[3.3 Compute Services]]

### Q35
Engineers already apply a Project tag to every resource. Finance wants monthly AWS costs broken down by project in the most detailed billing data available. What should the company do?

- A. Activate Project as a user-defined cost allocation tag and use the AWS Cost and Usage Report
- B. Create one budget per project in AWS Budgets
- C. Build one estimate per project in AWS Pricing Calculator
- D. Ask AWS Support to split the monthly invoice by project

> [!success]- Answer
> **A.** Tags appear in billing data only after they are activated as cost allocation tags, and the Cost and Usage Report is the most detailed cost and usage data.
> - B: Budgets alert on thresholds; they are not the most detailed cost data.
> - C: Pricing Calculator estimates future costs; it does not report actual spend.
> - D: AWS Support does not split invoices by tag; cost allocation tags do this.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q36
A developer needs to read objects from one S3 bucket named reports-prod. Which approach follows the principle of least privilege?

- A. Attach the AdministratorAccess AWS managed policy to the developer
- B. Attach the AmazonS3ReadOnlyAccess AWS managed policy to the developer
- C. Attach a customer managed policy that allows only s3:GetObject and s3:ListBucket on the reports-prod bucket
- D. Give the developer the root user's access keys

> [!success]- Answer
> **C.** A custom policy scoped to the exact actions and the single bucket grants only what the task needs.
> - A: AdministratorAccess grants full access to everything.
> - B: AmazonS3ReadOnlyAccess allows reading every bucket in the account, which is more than needed.
> - D: Root credentials have unrestricted access and must never be shared.
>
> Review: [[2.3 Access Management and IAM]]

### Q37
A team defines its runbooks and infrastructure as code, makes frequent, small, reversible changes, and holds reviews after each incident to improve its procedures. Which Well-Architected Framework pillar do these practices represent?

- A. Reliability
- B. Security
- C. Performance efficiency
- D. Operational excellence

> [!success]- Answer
> **D.** Performing operations as code, making frequent, small, reversible changes, and learning from operational failures are Operational excellence design principles.
> - A: Reliability principles include automatically recovering from failure and testing recovery procedures.
> - B: Security principles include a strong identity foundation and traceability.
> - C: Performance efficiency principles include using serverless architectures and experimenting more often.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q38
A company stores data in Amazon S3. Access patterns are unknown and change over time. It wants storage costs optimized automatically, with no retrieval fees and no operational effort. Which storage class should it use?

- A. S3 Standard-IA
- B. S3 Intelligent-Tiering
- C. S3 One Zone-IA
- D. S3 Glacier Flexible Retrieval

> [!success]- Answer
> **B.** Intelligent-Tiering moves objects between access tiers automatically based on access, with no retrieval fees (a small monitoring and automation charge applies per object).
> - A: Standard-IA charges retrieval fees and suits data known to be infrequently accessed.
> - C: One Zone-IA charges retrieval fees and keeps data in a single Availability Zone.
> - D: Glacier Flexible Retrieval is for archives with retrieval times of minutes to hours.
>
> Review: [[3.6 Storage Services]]

### Q39
Which TWO are examples of encryption in transit? (Select TWO.)

- A. Enabling server-side encryption with AWS KMS keys on an S3 bucket
- B. Serving a website over HTTPS with a certificate from AWS Certificate Manager (ACM)
- C. Encrypting an Amazon EBS volume
- D. Connecting a data center to a VPC through an AWS Site-to-Site VPN (IPsec) tunnel
- E. Turning on encryption for an Amazon RDS database

> [!success]- Answer
> **B and D.** HTTPS (TLS) and IPsec VPN tunnels both protect data while it moves across a network.
> - A: S3 server-side encryption protects data at rest.
> - C: EBS encryption protects data at rest.
> - E: RDS encryption protects data at rest.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q40
A bank keeps its core ledger in its own data center for regulatory reasons but runs its customer-facing web tier on AWS. The two are connected through AWS Direct Connect. Which deployment model is this?

- A. Cloud (all-in)
- B. Hybrid
- C. On-premises (private cloud)
- D. Multi-Region

> [!success]- Answer
> **B.** A hybrid deployment connects on-premises infrastructure with cloud resources.
> - A: An all-in cloud deployment runs everything in the cloud.
> - C: An on-premises deployment runs everything in the company's own data center.
> - D: Multi-Region describes how a cloud workload is spread across AWS Regions, not a deployment model.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q41
A company is migrating a Microsoft SQL Server database to AWS. It owns no SQL Server licenses and does not want to buy or track them. Which option meets this requirement?

- A. Run SQL Server on an EC2 Dedicated Host using Bring Your Own License (BYOL)
- B. Track licenses with AWS License Manager
- C. Download SQL Server licenses from AWS Artifact
- D. Use Amazon RDS for SQL Server with the license-included model

> [!success]- Answer
> **D.** With license-included pricing, the license cost is built into the hourly price, so the company buys and tracks nothing.
> - A: BYOL requires licenses the company does not have.
> - B: License Manager tracks licenses you own; it does not supply them.
> - C: Artifact provides compliance documents, not software licenses.
>
> Review: [[1.4 Cloud Economics]]

### Q42
A company uses a specific vendor's next-generation firewall on premises. It wants to deploy the same product in its VPC and have it billed by the hour on its AWS bill. Where should it get the product?

- A. AWS Marketplace
- B. AWS Partner Network
- C. AWS Service Catalog
- D. AWS Firewall Manager

> [!success]- Answer
> **A.** AWS Marketplace is the catalog of third-party software, including security products, with charges billed through the AWS account.
> - B: The Partner Network is the program for partner companies; it is not where you buy and deploy software.
> - C: Service Catalog distributes products your own IT team has approved; it is not a vendor store.
> - D: Firewall Manager centrally manages AWS firewall rules; it is not a third-party product.
>
> Review: [[2.4 Security Components and Resources]]

### Q43
Account A in an AWS Organizations consolidated billing family bought a Regional Reserved Instance for a Linux m5.large in us-east-1 but runs no matching instance. Account B in the same organization runs a matching instance. RI discount sharing is at its default setting. What happens?

- A. Account B pays On-Demand rates because RI discounts apply only in the purchasing account.
- B. AWS refunds the unused Reserved Instance to account A.
- C. The Reserved Instance discount can apply to account B's matching usage.
- D. Account B must buy its own Reserved Instance to receive any discount.

> [!success]- Answer
> **C.** In a consolidated billing family, Reserved Instance discounts are shared across accounts by default, so unused RI benefit applies to matching usage in other accounts.
> - A: Sharing is on by default; discounts are not limited to the purchasing account.
> - B: Reserved Instances are not refunded for unused time.
> - D: Account B benefits from account A's RI without its own purchase.
>
> Review: [[4.1 AWS Pricing Models]]

### Q44
Instances in a private subnet must download software updates from the internet but must not accept connections initiated from the internet. What should be added to the VPC?

- A. An internet gateway, with the private subnet's instances given public IP addresses
- B. A NAT gateway in a public subnet, with the private subnet's route table pointing to it
- C. A virtual private gateway
- D. A customer gateway

> [!success]- Answer
> **B.** A NAT gateway lets instances in a private subnet start outbound connections to the internet while blocking connections started from the internet.
> - A: Public IP addresses with an internet gateway route make instances reachable from the internet, so they are no longer private.
> - C: A virtual private gateway is the AWS side of a Site-to-Site VPN.
> - D: A customer gateway is the on-premises side of a Site-to-Site VPN.
>
> Review: [[3.5 Network Services]]

### Q45
A US company wants to launch its application in Japan so that Japanese users get low latency. It does not want to build or lease data centers there and wants to be live within days. Which AWS Cloud benefit does this describe?

- A. Going global in minutes by deploying to AWS Regions worldwide
- B. Economies of scale
- C. Elasticity
- D. High availability

> [!success]- Answer
> **A.** AWS's global infrastructure lets a company deploy in another Region quickly, putting its application near new users without building facilities.
> - B: Economies of scale explain lower prices, not faster global deployment.
> - C: Elasticity is scaling capacity up and down with demand.
> - D: High availability is about staying available through failures.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q46
Under the AWS shared responsibility model, which is a shared control, where AWS and the customer each have responsibilities in their own layer?

- A. Physical and environmental controls
- B. Hypervisor security
- C. Patch management
- D. Customer data classification

> [!success]- Answer
> **C.** Patch management is shared: AWS patches the infrastructure, and customers patch their guest operating systems and applications. Configuration management and training are the other shared controls.
> - A: Physical and environmental controls belong to AWS.
> - B: Hypervisor security belongs to AWS.
> - D: Classifying customer data belongs to the customer.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q47
A company stores application logs in S3 Standard. Logs are read often for the first 30 days and rarely between days 30 and 90. After 90 days they are kept for seven years for compliance, and a retrieval time of up to 48 hours is acceptable. Which TWO lifecycle actions minimize cost while meeting these requirements? (Select TWO.)

- A. Transition objects to S3 One Zone-IA on the day they are created
- B. Transition objects to S3 Standard-IA after 30 days
- C. Copy objects to Amazon EBS volumes after 30 days
- D. Expire (delete) objects after 90 days
- E. Transition objects to S3 Glacier Deep Archive after 90 days

> [!success]- Answer
> **B and E.** Standard-IA lowers cost for rarely read data from day 30, and Glacier Deep Archive is the lowest-cost class for long-term retention, with retrieval within 48 hours.
> - A: Logs are read often in the first 30 days, so IA retrieval fees would apply, and S3 Lifecycle does not move objects to an IA class before they are 30 days old.
> - C: EBS volumes cost more than S3 for this and are not a lifecycle target.
> - D: Deleting at 90 days breaks the seven-year retention requirement.
>
> Review: [[3.6 Storage Services]]

### Q48
An external auditing firm works in its own AWS account. Its team needs temporary read-only access to resources in the company's account. What is the most secure approach?

- A. Create IAM users in the company's account and send the auditors long-term access keys
- B. Share the root user credentials, protected by MFA
- C. Add the auditing firm's account to an IAM group in the company's account
- D. Create an IAM role in the company's account with read-only permissions and a trust policy that lets the auditing firm's account assume it

> [!success]- Answer
> **D.** A cross-account IAM role gives temporary credentials with only the permissions in the role, and no long-term keys are shared.
> - A: Long-term access keys sent to outsiders are a credential exposure risk.
> - B: Root credentials must never be shared.
> - C: IAM groups contain IAM users only; another account cannot be added to a group.
>
> Review: [[2.3 Access Management and IAM]]

### Q49
A company manually builds an identical test environment in the console every week. It takes hours and produces inconsistent configurations. What is the main economic benefit of defining the environment in AWS CloudFormation templates?

- A. CloudFormation removes the charges for the resources it creates.
- B. Provisioning becomes repeatable and fast, reducing labor and the cost of configuration errors.
- C. CloudFormation automatically buys Reserved Instances for the resources.
- D. CloudFormation moves responsibility for operating system patching to AWS.

> [!success]- Answer
> **B.** Infrastructure as code automates provisioning, so environments are built the same way every time in minutes, saving staff time and avoiding errors.
> - A: You still pay for the resources CloudFormation creates.
> - C: CloudFormation does not purchase Reserved Instances.
> - D: CloudFormation does not change the shared responsibility model.
>
> Review: [[1.4 Cloud Economics]]

### Q50
A media company wants to ingest website clickstream events in near real time and give business users interactive dashboards built from the results. Which TWO services should it use? (Select TWO.)

- A. AWS Glue
- B. Amazon Athena
- C. Amazon Kinesis
- D. Amazon SageMaker
- E. Amazon QuickSight

> [!success]- Answer
> **C and E.** Kinesis collects and processes streaming data in near real time, and QuickSight provides business intelligence dashboards.
> - A: Glue is a serverless ETL and data catalog service, not a real-time ingestion or dashboard service.
> - B: Athena runs SQL queries on data in S3; it neither ingests streams nor builds dashboards.
> - D: SageMaker builds and trains machine learning models.
>
> Current status: QuickSight is now AWS Quick Sight, part of AWS Quick. The exam uses "Amazon QuickSight".
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q51
An AWS reseller manages many customer accounts in one organization. It must present each customer with a pro forma bill that uses the reseller's own custom rates. Which service supports this?

- A. AWS Billing Conductor
- B. AWS Cost Explorer
- C. AWS Budgets
- D. AWS Organizations consolidated billing on its own

> [!success]- Answer
> **A.** Billing Conductor groups accounts and applies custom pricing to produce pro forma bills for showback and chargeback.
> - B: Cost Explorer shows actual AWS costs; it does not apply custom rates.
> - C: Budgets sends alerts on spend thresholds.
> - D: Consolidated billing produces one bill at AWS rates for the whole organization.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q52
Before a PCI DSS audit, a company wants to automatically and continuously collect evidence from its own AWS accounts, mapped to PCI DSS controls, and generate assessment reports for its auditors. Which service should it use?

- A. AWS Artifact
- B. Amazon Inspector
- C. AWS Config
- D. AWS Audit Manager

> [!success]- Answer
> **D.** Audit Manager continuously collects evidence of the customer's AWS usage, maps it to frameworks such as PCI DSS, and produces assessment reports.
> - A: Artifact provides AWS's own compliance reports, not evidence about the customer's resources.
> - B: Inspector scans for software vulnerabilities.
> - C: Config evaluates resource configurations; it is one evidence source but does not organize evidence into audit assessments.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q53
A company's relational database requires a third-party monitoring agent installed on the database server's operating system and full control over engine settings that a managed database service does not expose. Which option meets these requirements?

- A. Amazon RDS
- B. Amazon Aurora
- C. A database installed on Amazon EC2 instances
- D. Amazon DynamoDB

> [!success]- Answer
> **C.** Running the database on EC2 gives full control of the operating system and engine, in exchange for managing patching, backups, and scaling yourself.
> - A: Standard Amazon RDS does not give access to the host operating system.
> - B: Aurora is a managed service with no operating system access.
> - D: DynamoDB is a managed NoSQL service, not a relational database.
>
> Review: [[3.4 Database Services]]

### Q54
A company moves its self-managed on-premises MySQL database to Amazon RDS for MySQL to gain automated backups and patching. It makes no changes to the application code. Which migration strategy is this?

- A. Rehost
- B. Replatform
- C. Refactor
- D. Repurchase

> [!success]- Answer
> **B.** Replatform ("lift, tinker, and shift") moves to a managed platform for a benefit without changing the application's core architecture.
> - A: Rehost would move the database as is, for example onto an EC2 instance.
> - C: Refactor re-architects the application, often to cloud-native services.
> - D: Repurchase replaces the application with a different product, typically SaaS.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q55
A company stores data in Amazon DynamoDB. Which task is the company's responsibility?

- A. Controlling which IAM principals and services can access the tables
- B. Patching the storage nodes
- C. Replicating data across multiple Availability Zones in the Region
- D. Maintaining server hardware

> [!success]- Answer
> **A.** For DynamoDB, the customer decides who and what can access its tables and manages its data.
> - B: AWS patches the infrastructure behind DynamoDB.
> - C: DynamoDB replicates data across multiple Availability Zones automatically.
> - D: Hardware is always AWS's responsibility.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q56
A web application runs on Amazon EC2. It must automatically add instances when demand rises and spread incoming traffic across healthy instances in multiple Availability Zones. Which TWO services provide these capabilities? (Select TWO.)

- A. Amazon CloudWatch
- B. Amazon EC2 Auto Scaling
- C. AWS Batch
- D. Elastic Load Balancing
- E. Amazon Elastic Container Registry (Amazon ECR)

> [!success]- Answer
> **B and D.** EC2 Auto Scaling adds and removes instances to match demand, and Elastic Load Balancing distributes traffic across healthy instances in multiple Availability Zones.
> - A: CloudWatch supplies metrics and alarms that can trigger scaling, but it neither launches instances nor distributes traffic.
> - C: AWS Batch runs batch computing jobs.
> - E: ECR stores container images.
>
> Review: [[3.3 Compute Services]]

### Q57
Which TWO are design principles of the Security pillar of the AWS Well-Architected Framework? (Select TWO.)

- A. Implement a strong identity foundation
- B. Stop guessing capacity
- C. Adopt a consumption model
- D. Enable traceability
- E. Use serverless architectures

> [!success]- Answer
> **A and D.** A strong identity foundation and traceability are Security pillar design principles.
> - B: Stop guessing capacity is a Reliability principle.
> - C: Adopt a consumption model is a Cost optimization principle.
> - E: Use serverless architectures is a Performance efficiency principle.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q58
A company must connect its data center to a VPC today, with traffic encrypted. It cannot wait weeks for a dedicated circuit and accepts connectivity over the internet. Which option should it use?

- A. AWS Direct Connect
- B. AWS Client VPN
- C. VPC peering
- D. AWS Site-to-Site VPN

> [!success]- Answer
> **D.** Site-to-Site VPN creates an encrypted IPsec tunnel over the internet between an on-premises network and a VPC and can be set up quickly.
> - A: Direct Connect is a dedicated private connection that typically takes weeks to provision and is not encrypted by default.
> - B: Client VPN connects individual users' devices, not a whole data center network.
> - C: VPC peering connects two VPCs, not an on-premises network.
>
> Review: [[3.5 Network Services]]

### Q59
An application has its database password hard-coded in its source code. Security requires that the password be stored centrally, retrieved at runtime, and rotated automatically every 30 days. Which service should be used?

- A. AWS Key Management Service (AWS KMS)
- B. AWS CloudHSM
- C. AWS Secrets Manager
- D. AWS Certificate Manager (ACM)

> [!success]- Answer
> **C.** Secrets Manager stores credentials, returns them to applications at runtime, and rotates them automatically on a schedule.
> - A: KMS manages encryption keys, not application passwords.
> - B: CloudHSM provides dedicated hardware for cryptographic keys, not password storage and rotation.
> - D: ACM manages SSL/TLS certificates.
>
> Review: [[2.3 Access Management and IAM]]

### Q60
A company wants a response within 30 minutes when a business-critical system is down and access to a pool of Technical Account Managers. It wants the lowest-cost plan that meets these needs. Which support plan should it choose?

- A. Business
- B. Enterprise On-Ramp
- C. Enterprise
- D. Developer

> [!success]- Answer
> **B.** Enterprise On-Ramp offers a 30-minute response for business-critical system down and access to a pool of TAMs.
> - A: Business has no business-critical response time (its fastest is under 1 hour for production system down) and no TAM.
> - C: Enterprise meets the needs, with a designated TAM and 15-minute response, but costs more.
> - D: Developer offers business-hours web access with no TAM.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q61
Contractors use their personal laptops. They need a full, persistent Windows desktop with the company's applications, with no company data stored on their devices. Which service should the company use?

- A. Amazon WorkSpaces
- B. Amazon AppStream 2.0
- C. Amazon WorkSpaces Web
- D. Amazon Lightsail

> [!success]- Answer
> **A.** WorkSpaces provides persistent virtual desktops in the cloud that users reach from their own devices.
> - B: AppStream 2.0 streams individual applications, not a full persistent desktop.
> - C: WorkSpaces Web provides secure browser access to internal websites and SaaS applications only.
> - D: Lightsail provides simple virtual servers, not managed desktops for end users.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q62
Developers can launch a test environment in minutes, try a new feature, and delete everything if the experiment fails, at little cost. Which AWS Cloud benefit does this describe?

- A. Elasticity
- B. High availability
- C. Economies of scale
- D. Agility

> [!success]- Answer
> **D.** Agility is the ability to get resources quickly and experiment cheaply, which speeds innovation.
> - A: Elasticity is scaling capacity automatically as demand changes.
> - B: High availability is staying accessible despite failures.
> - C: Economies of scale explain AWS's lower prices.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q63
Which service checks an AWS account for security groups that allow unrestricted access to specific ports, a root user without MFA, and exposed access keys, and also makes cost optimization and service quota recommendations?

- A. Amazon Inspector
- B. AWS Trusted Advisor
- C. Amazon GuardDuty
- D. Amazon Macie

> [!success]- Answer
> **B.** Trusted Advisor inspects the account against best practices in categories including security, cost optimization, and service limits.
> - A: Inspector scans EC2, container images, and Lambda for software vulnerabilities and network exposure; it makes no cost recommendations.
> - C: GuardDuty detects active threats from log data.
> - D: Macie discovers sensitive data in S3.
>
> Review: [[2.4 Security Components and Resources]]

### Q64
Which TWO are valid reasons to deploy a workload in more than one AWS Region? (Select TWO.)

- A. To reduce data transfer charges between the application's tiers
- B. Because Amazon RDS Multi-AZ deployments require a second Region
- C. To meet a law that requires a copy of customer data to stay in a specific country
- D. Because AWS Business Support requires workloads in at least two Regions
- E. To recover if an entire Region becomes unavailable

> [!success]- Answer
> **C and E.** Data sovereignty requirements and disaster recovery from a Region-wide outage are both reasons to use multiple Regions.
> - A: Traffic between Regions is charged, so splitting tiers across Regions raises data transfer costs.
> - B: RDS Multi-AZ uses multiple Availability Zones within one Region.
> - D: No support plan requires multiple Regions.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q65
A company runs Kubernetes on premises, and its staff spend significant time operating the Kubernetes control plane. Which AWS option most reduces this operational cost while keeping Kubernetes?

- A. Install Kubernetes on Amazon EC2 instances
- B. AWS Elastic Beanstalk
- C. Amazon Elastic Kubernetes Service (Amazon EKS)
- D. Amazon Elastic Container Service (Amazon ECS)

> [!success]- Answer
> **C.** EKS is a managed service in which AWS runs the Kubernetes control plane, removing that operational work.
> - A: Self-installed Kubernetes on EC2 keeps all control plane operations with the company.
> - B: Elastic Beanstalk deploys web applications; it is not a Kubernetes service.
> - D: ECS is AWS's own container orchestrator, not Kubernetes.
>
> Review: [[1.4 Cloud Economics]]

---

## Scoring table

Mark each question 1 (correct) or 0 (wrong). Select TWO questions score 1 only if both choices are right.

| Q | Domain | Task statement | Answer | Score |
|---|---|---|---|---|
| 1 | 3 | 3.3 Compute | C | |
| 2 | 2 | 2.2 Security, governance, compliance | A | |
| 3 | 1 | 1.1 Benefits | B | |
| 4 | 3 | 3.8 Other in-scope services | D | |
| 5 | 2 | 2.1 Shared responsibility | C | |
| 6 | 4 | 4.2 Billing and cost management | B | |
| 7 | 1 | 1.2 Well-Architected | D | |
| 8 | 3 | 3.4 Database | B, C | |
| 9 | 2 | 2.4 Security components | A | |
| 10 | 3 | 3.2 Global infrastructure | D | |
| 11 | 1 | 1.4 Cloud economics | C | |
| 12 | 2 | 2.3 Access management | A, C | |
| 13 | 4 | 4.1 Pricing models | A | |
| 14 | 3 | 3.5 Network | B | |
| 15 | 2 | 2.2 Security, governance, compliance | D | |
| 16 | 1 | 1.3 Migration and CAF | B | |
| 17 | 3 | 3.6 Storage | A | |
| 18 | 2 | 2.3 Access management | C | |
| 19 | 3 | 3.1 Deploying and operating | B | |
| 20 | 1 | 1.2 Well-Architected | D | |
| 21 | 4 | 4.1 Pricing models | A, D | |
| 22 | 2 | 2.1 Shared responsibility | B, E | |
| 23 | 3 | 3.4 Database | B | |
| 24 | 1 | 1.4 Cloud economics | D | |
| 25 | 2 | 2.4 Security components | A | |
| 26 | 3 | 3.2 Global infrastructure | C | |
| 27 | 1 | 1.3 Migration and CAF | C | |
| 28 | 4 | 4.3 Support and resources | B | |
| 29 | 3 | 3.7 AI/ML and analytics | A | |
| 30 | 2 | 2.1 Shared responsibility | D | |
| 31 | 3 | 3.5 Network | C | |
| 32 | 1 | 1.1 Benefits | B, D | |
| 33 | 2 | 2.2 Security, governance, compliance | B | |
| 34 | 3 | 3.3 Compute | A | |
| 35 | 4 | 4.2 Billing and cost management | A | |
| 36 | 2 | 2.3 Access management | C | |
| 37 | 1 | 1.2 Well-Architected | D | |
| 38 | 3 | 3.6 Storage | B | |
| 39 | 2 | 2.2 Security, governance, compliance | B, D | |
| 40 | 3 | 3.1 Deploying and operating | B | |
| 41 | 1 | 1.4 Cloud economics | D | |
| 42 | 2 | 2.4 Security components | A | |
| 43 | 4 | 4.1 Pricing models | C | |
| 44 | 3 | 3.5 Network | B | |
| 45 | 1 | 1.1 Benefits | A | |
| 46 | 2 | 2.1 Shared responsibility | C | |
| 47 | 3 | 3.6 Storage | B, E | |
| 48 | 2 | 2.3 Access management | D | |
| 49 | 1 | 1.4 Cloud economics | B | |
| 50 | 3 | 3.7 AI/ML and analytics | C, E | |
| 51 | 4 | 4.2 Billing and cost management | A | |
| 52 | 2 | 2.2 Security, governance, compliance | D | |
| 53 | 3 | 3.4 Database | C | |
| 54 | 1 | 1.3 Migration and CAF | B | |
| 55 | 2 | 2.1 Shared responsibility | A | |
| 56 | 3 | 3.3 Compute | B, D | |
| 57 | 1 | 1.2 Well-Architected | A, D | |
| 58 | 3 | 3.5 Network | D | |
| 59 | 2 | 2.3 Access management | C | |
| 60 | 4 | 4.3 Support and resources | B | |
| 61 | 3 | 3.8 Other in-scope services | A | |
| 62 | 1 | 1.1 Benefits | D | |
| 63 | 2 | 2.4 Security components | B | |
| 64 | 3 | 3.2 Global infrastructure | C, E | |
| 65 | 1 | 1.4 Cloud economics | C | |

### Totals by domain

| Domain | Questions | Your score | Percent | Target (90%) |
|---|---|---|---|---|
| 1 Cloud Concepts | 3, 7, 11, 16, 20, 24, 27, 32, 37, 41, 45, 49, 54, 57, 62, 65 | /16 | | 15 |
| 2 Security and Compliance | 2, 5, 9, 12, 15, 18, 22, 25, 30, 33, 36, 39, 42, 46, 48, 52, 55, 59, 63 | /19 | | 17 |
| 3 Cloud Technology and Services | 1, 4, 8, 10, 14, 17, 19, 23, 26, 29, 31, 34, 38, 40, 44, 47, 50, 53, 56, 58, 61, 64 | /22 | | 20 |
| 4 Billing, Pricing, and Support | 6, 13, 21, 28, 35, 43, 51, 60 | /8 | | 7 |
| **Total** | 65 | /65 | | 59 |

Questions per task statement: 1.1 ×4, 1.2 ×4, 1.3 ×3, 1.4 ×5; 2.1 ×5, 2.2 ×5, 2.3 ×5, 2.4 ×4; 3.1 ×2, 3.2 ×3, 3.3 ×3, 3.4 ×3, 3.5 ×4, 3.6 ×3, 3.7 ×2, 3.8 ×2; 4.1 ×3, 4.2 ×3, 4.3 ×2.

Any domain below 80%: reread that domain's task notes, then drill the matching flashcard deck and practice set ([[Practice - Domain 1]], [[Practice - Domain 2]], [[Practice - Domain 3 (Part 1)]], [[Practice - Domain 3 (Part 2)]], [[Practice - Domain 4]]). For look-alike misses, use [[Commonly Confused Services]].
