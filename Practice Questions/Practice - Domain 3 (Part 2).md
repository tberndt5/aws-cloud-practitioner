---
tags:
  - clf-c02
  - practice
  - domain-3
---
# Practice - Domain 3 (Part 2)

Twenty original questions on task statements 3.5 to 3.8. Answer each before opening the collapsed callout. Notes: [[3.5 Network Services]] · [[3.6 Storage Services]] · [[3.7 AI-ML and Analytics Services]] · [[3.8 Other In-Scope Service Categories]]

### Q1
A company runs application servers in a private subnet of a VPC. The servers must download operating system patches from the internet, but nothing on the internet should be able to start a connection to them. Which component meets this requirement?

- A. Internet gateway attached to the private subnet's route table
- B. NAT gateway in a public subnet
- C. Virtual private gateway
- D. VPC peering connection

> [!success]- Answer
> **B.** A NAT gateway, placed in a public subnet, lets instances in a private subnet make outbound connections while blocking connections started from the internet.
> - A: Routing a subnet to an internet gateway makes it public and allows two-way access, which breaks the requirement.
> - C: A virtual private gateway is the AWS end of a Site-to-Site VPN, not an internet path.
> - D: VPC peering connects two VPCs; it gives no internet access.
>
> Review: [[3.5 Network Services]]

### Q2
A security team discovers that a known malicious IP address range is sending traffic to every instance in one subnet. They want to block that range for the whole subnet. What should they use?

- A. A security group deny rule
- B. AWS Shield Advanced
- C. A network ACL deny rule
- D. An IAM policy

> [!success]- Answer
> **C.** Network ACLs apply at the subnet level and support explicit deny rules.
> - A: Security groups support allow rules only; there is no deny rule.
> - B: Shield Advanced protects against DDoS attacks; it is not how you block a specific IP range from a subnet.
> - D: IAM policies control access to AWS API actions, not network traffic.
>
> Review: [[3.5 Network Services]]

### Q3
A company needs a connection between its data center and AWS that does not travel over the public internet and provides consistent network performance for large daily data transfers. Which service should it use?

- A. AWS Site-to-Site VPN
- B. AWS Direct Connect
- C. Amazon CloudFront
- D. AWS Client VPN

> [!success]- Answer
> **B.** AWS Direct Connect is a private, dedicated network connection from on premises to AWS with consistent performance.
> - A: Site-to-Site VPN is encrypted but runs over the public internet, so performance varies.
> - C: CloudFront is a CDN for delivering content to end users.
> - D: Client VPN connects individual users' devices, over the internet.
>
> Review: [[3.5 Network Services]]

### Q4
A global online game uses UDP traffic. The company wants players to connect through two fixed IP addresses and be routed over the AWS global network to the nearest healthy Regional endpoint. Which service meets these requirements?

- A. Amazon CloudFront
- B. Amazon Route 53 latency-based routing
- C. AWS Global Accelerator
- D. Elastic Load Balancing

> [!success]- Answer
> **C.** Global Accelerator provides two static anycast IP addresses and routes TCP and UDP traffic over the AWS backbone to the best healthy endpoint.
> - A: CloudFront caches HTTP(S) content and does not provide static anycast IPs for UDP applications.
> - B: Route 53 answers DNS queries; it does not provide static IPs or carry traffic over the AWS network.
> - D: A load balancer distributes traffic within a Region, not globally through edge locations.
>
> Review: [[3.5 Network Services]]

### Q5
Which of the following are functions of Amazon Route 53? (Select TWO.)

- A. Registering domain names
- B. Caching static content at edge locations
- C. Checking the health of endpoints and routing around failures
- D. Encrypting traffic between VPCs
- E. Filtering malicious HTTP requests

> [!success]- Answer
> **A and C.** Route 53 is a DNS service for domain registration, DNS routing, and health checking.
> - B: Caching at edge locations is Amazon CloudFront.
> - D: Route 53 does not encrypt traffic; VPN or TLS does.
> - E: Filtering HTTP requests is AWS WAF.
>
> Review: [[3.5 Network Services]]

### Q6
A hospital stores X-ray images that are viewed only a few times a year, but when a doctor requests one it must load in milliseconds. The hospital wants the lowest storage cost that meets this need. Which S3 storage class should it use?

- A. S3 Standard
- B. S3 Glacier Flexible Retrieval
- C. S3 Glacier Deep Archive
- D. S3 Glacier Instant Retrieval

> [!success]- Answer
> **D.** S3 Glacier Instant Retrieval is built for long-lived, rarely accessed data that still needs millisecond retrieval, at lower storage cost than Standard or Standard-IA.
> - A: S3 Standard gives milliseconds but costs more for data accessed this rarely.
> - B: Glacier Flexible Retrieval needs minutes to hours to restore.
> - C: Glacier Deep Archive needs up to 12 hours (Standard) or 48 hours (Bulk).
>
> Review: [[3.6 Storage Services]]

### Q7
A company must keep financial records for 10 years to meet regulations. The records will almost never be read, and a retrieval time of up to 48 hours is acceptable. Which storage option has the lowest cost?

- A. S3 Glacier Deep Archive
- B. S3 One Zone-IA
- C. S3 Intelligent-Tiering
- D. Amazon EBS Cold HDD (sc1)

> [!success]- Answer
> **A.** S3 Glacier Deep Archive is the lowest-cost S3 storage class, designed for long-term retention with retrieval within 12 to 48 hours.
> - B: One Zone-IA costs more and stores data in a single AZ, which is risky for the only copy of records.
> - C: Intelligent-Tiering adds monitoring fees and is meant for unknown access patterns, not known archival data.
> - D: EBS is block storage attached to EC2 in one AZ and is far more expensive per GB for archives.
>
> Review: [[3.6 Storage Services]]

### Q8
A company stores thumbnail images that it can regenerate from originals at any time. The thumbnails are accessed about once a month. Which S3 storage class is most cost-effective?

- A. S3 Standard
- B. S3 Standard-IA
- C. S3 One Zone-IA
- D. S3 Glacier Flexible Retrieval

> [!success]- Answer
> **C.** S3 One Zone-IA is the cheapest millisecond-access class for infrequently accessed data that can be re-created, because it stores data in a single AZ.
> - A: Standard is priced for frequent access.
> - B: Standard-IA stores data across at least three AZs, which costs more than needed for re-creatable data.
> - D: Glacier Flexible Retrieval requires a restore that takes minutes to hours.
>
> Review: [[3.6 Storage Services]]

### Q9
A team writes application logs to Amazon S3. Logs are read often during the first 30 days, rarely for the next year, and must then be deleted. What is the simplest way to reduce cost and meet this policy?

- A. Enable S3 Versioning
- B. Configure S3 Cross-Region Replication
- C. Create an S3 Lifecycle configuration with transition and expiration rules
- D. Use AWS Backup to copy the logs to another account

> [!success]- Answer
> **C.** Lifecycle rules can transition objects to cheaper classes after 30 days and expire (delete) them after a set age, automatically.
> - A: Versioning keeps old copies, which increases storage cost.
> - B: Replication copies data to another Region; it does not tier or delete.
> - D: AWS Backup centralizes backups; it does not move S3 objects between classes or delete them on a schedule.
>
> Review: [[3.6 Storage Services]]

### Q10
An application on an EC2 instance needs fast temporary storage for a cache. Losing the data when the instance stops is acceptable, and the company wants to avoid paying for extra storage. Which option fits best?

- A. Amazon EBS General Purpose SSD volume
- B. EC2 instance store
- C. Amazon EFS
- D. Amazon S3 Standard

> [!success]- Answer
> **B.** Instance store is physically attached to the host, very fast, included in the instance price, and ephemeral, which suits a cache.
> - A: EBS persists after stop and is billed separately; persistence is not needed here.
> - C: EFS is a shared network file system billed per GB, not local temporary storage.
> - D: S3 is object storage reached over an API, not a local cache disk.
>
> Review: [[3.6 Storage Services]]

### Q11
A company has on-premises applications that write files to a local file share. It wants those files stored durably in Amazon S3 while keeping fast local access to recently used files. Which service should it use?

- A. AWS Storage Gateway (S3 File Gateway)
- B. Amazon FSx for Lustre
- C. AWS Snowball Edge
- D. Amazon EBS snapshots

> [!success]- Answer
> **A.** S3 File Gateway presents NFS or SMB file shares on premises, stores files as S3 objects, and keeps a local cache of recently used data.
> - B: FSx for Lustre is a high-performance file system in AWS for HPC, not an on-premises cached share.
> - C: Snowball Edge is for one-time offline transfer or edge compute, not ongoing hybrid access.
> - D: EBS snapshots back up EBS volumes attached to EC2.
>
> Review: [[3.6 Storage Services]]

### Q12
A company wants one service to define backup schedules and retention rules and apply them across Amazon EBS volumes, Amazon RDS databases, Amazon DynamoDB tables, and Amazon EFS file systems. Which service should it use?

- A. AWS Elastic Disaster Recovery
- B. AWS Backup
- C. AWS Storage Gateway
- D. Amazon S3 Lifecycle

> [!success]- Answer
> **B.** AWS Backup centralizes and automates backups across many AWS services and on-premises storage using backup plans.
> - A: Elastic Disaster Recovery continuously replicates servers for fast failover; it is not a policy-based backup manager for databases and file systems.
> - C: Storage Gateway connects on-premises applications to cloud storage.
> - D: Lifecycle rules manage S3 objects only.
>
> Review: [[3.6 Storage Services]]

### Q13
Which of the following are file storage services? (Select TWO.)

- A. Amazon EBS
- B. Amazon EFS
- C. Amazon S3
- D. Amazon FSx for Windows File Server
- E. EC2 instance store

> [!success]- Answer
> **B and D.** EFS (NFS, Linux) and FSx for Windows File Server (SMB, Windows) are managed file systems that many clients share.
> - A: EBS is block storage.
> - C: S3 is object storage.
> - E: Instance store is block storage on the host.
>
> Review: [[3.6 Storage Services]]

### Q14
A retailer wants to analyze thousands of product reviews to find out whether customers feel positively or negatively about each product. The team has no machine learning experience. Which service should it use?

- A. Amazon SageMaker
- B. Amazon Kendra
- C. Amazon Comprehend
- D. Amazon Rekognition

> [!success]- Answer
> **C.** Amazon Comprehend uses natural language processing to extract insights such as sentiment from text, with no ML expertise needed.
> - A: SageMaker is for building custom models, which needs ML skills.
> - B: Kendra is intelligent search over documents, not sentiment analysis.
> - D: Rekognition analyzes images and video.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q15
An insurance company receives thousands of scanned claim forms each day and wants to automatically pull out the policy number, dates, and table data from each form. Which service should it use?

- A. Amazon Textract
- B. Amazon Transcribe
- C. Amazon Translate
- D. Amazon Polly

> [!success]- Answer
> **A.** Textract extracts text, handwriting, form fields, and tables from scanned documents.
> - B: Transcribe converts speech in audio to text.
> - C: Translate converts text between languages.
> - D: Polly converts text to speech.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q16
A data analyst wants to run standard SQL queries against CSV and Parquet files already stored in Amazon S3 without setting up servers or loading the data into a database. Which service should the analyst use?

- A. Amazon Redshift
- B. Amazon QuickSight
- C. Amazon EMR
- D. Amazon Athena

> [!success]- Answer
> **D.** Athena is serverless and runs standard SQL directly on data in S3, charging per query.
> - A: Redshift is a data warehouse that requires provisioning and loading data.
> - B: QuickSight builds dashboards; it visualizes results rather than querying S3 files with SQL itself.
> - C: EMR runs Hadoop and Spark clusters that you configure.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q17
A company wants to ingest website clickstream data in near real time and then build executive dashboards from it. Which combination of services fits? (Select TWO.)

- A. Amazon Kinesis
- B. Amazon QuickSight
- C. Amazon Lex
- D. Amazon Polly
- E. AWS Data Exchange

> [!success]- Answer
> **A and B.** Kinesis collects and processes streaming data in near real time; QuickSight creates business intelligence dashboards.
> - C: Lex builds chatbots.
> - D: Polly converts text to speech.
> - E: Data Exchange is for subscribing to third-party data sets.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q18
An order-processing application has a web tier that sometimes receives bursts of orders faster than the back-end tier can process them. The company wants to decouple the tiers so no orders are lost during bursts. Which service should it use?

- A. Amazon SNS
- B. Amazon SES
- C. Amazon Connect
- D. Amazon SQS

> [!success]- Answer
> **D.** SQS stores messages in a queue until the back end polls and processes them, decoupling the tiers and absorbing bursts.
> - A: SNS pushes messages to subscribers immediately and does not hold them for later processing.
> - B: SES sends email.
> - C: Connect is a contact center service.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q19
A development team wants to find which microservice is causing slow responses in its distributed application by following individual requests from end to end. Which service should it use?

- A. AWS CloudTrail
- B. AWS CodeDeploy
- C. AWS X-Ray
- D. AWS AppConfig

> [!success]- Answer
> **C.** X-Ray traces requests through distributed applications and shows a service map to find bottlenecks and errors.
> - A: CloudTrail records API calls made in the account, not application request paths.
> - B: CodeDeploy automates deployments.
> - D: AppConfig deploys configuration and feature flags.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q20
A design firm wants to give contractors access to one CAD application from their own laptops through a web browser, without installing the application locally or providing full desktops. Which service should it use?

- A. Amazon WorkSpaces
- B. Amazon AppStream 2.0
- C. Amazon WorkSpaces Web
- D. AWS Amplify

> [!success]- Answer
> **B.** AppStream 2.0 streams individual desktop applications to users' browsers.
> - A: WorkSpaces provides a full virtual desktop, more than is needed.
> - C: WorkSpaces Web provides secure access to internal websites and SaaS apps, not desktop applications like CAD.
> - D: Amplify builds and hosts web and mobile apps.
>
> Review: [[3.8 Other In-Scope Service Categories]]
