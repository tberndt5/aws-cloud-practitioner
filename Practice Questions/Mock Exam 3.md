---
tags:
  - clf-c02
  - practice
  - mock-exam
---
# Mock Exam 3

> [!info] Instructions
> - **65 questions, 90 minutes, closed book.** Set a timer and do not open the answers until you finish all 65.
> - This is the final timed run, planned for the day before the exam. It tests the same blueprint as [[Mock Exam 1]] and [[Mock Exam 2]] with entirely different questions, at the difficulty of Mock Exam 1 (the real exam's level). Many correct answers are services and facts the first two mocks did not use as answers.
> - The real exam scores 50 questions and includes 15 unscored ones you cannot identify, reported as a scaled score of 100–1,000. **700 passes**, roughly 70% correct. Your target here is **90% (59 of 65)**.
> - There is no penalty for guessing. Never leave a question blank.
> - "Select TWO" questions need both correct answers to score. There are 11 of them.
> - Domain weighting matches the exam guide: Domain 1 = 16 questions, Domain 2 = 19, Domain 3 = 22, Domain 4 = 8, interleaved as on the real exam.
> - When you finish, mark each answer right or wrong in the [[#Scoring table]] and total each domain. Reread the task note linked in each Review line for every miss.

> [!note] Support plan names
> This exam uses the support plans in the CLF-C02 exam guide (Basic, Developer, Business, Enterprise On-Ramp, Enterprise). Current status: AWS stopped selling Developer and Business Support to new subscribers on December 2, 2025, and those plans and Enterprise On-Ramp end on January 1, 2027 (replaced by Business Support+, Enterprise, and Unified Operations). The exam still tests the older names.

---

### Q1
A machine learning team trains deep learning models on Amazon EC2. Training runs much faster on graphics processing units (GPUs). Which EC2 instance category should the team choose?

- A. General purpose
- B. Compute optimized
- C. Memory optimized
- D. Accelerated computing

> [!success]- Answer
> **D.** Accelerated computing instances use hardware accelerators such as GPUs for machine learning training, graphics processing, and similar work.
> - A: General purpose instances balance compute, memory, and networking for workloads such as web servers; they have no GPUs.
> - B: Compute optimized instances have fast CPUs for CPU-bound work such as batch processing and media transcoding, not GPUs.
> - C: Memory optimized instances suit large in-memory data sets, such as in-memory databases.
>
> Review: [[3.3 Compute Services]]

### Q2
A company wants to encrypt data at rest in Amazon EBS volumes, Amazon S3 buckets, and Amazon RDS databases with encryption keys that it creates and controls. It wants a managed service that integrates with these services and records every use of a key in AWS CloudTrail. Which service should it use?

- A. AWS Secrets Manager
- B. AWS Key Management Service (AWS KMS)
- C. AWS Certificate Manager (ACM)
- D. Amazon Macie

> [!success]- Answer
> **B.** AWS KMS creates and controls the cryptographic keys that protect data, integrates with most AWS services that store data, and logs key use in CloudTrail.
> - A: Secrets Manager stores and rotates secrets such as database passwords; it is not the key service that encrypts EBS, S3, and RDS.
> - C: ACM issues and renews SSL/TLS certificates for encryption in transit.
> - D: Macie discovers sensitive data in S3; it does not encrypt anything.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q3
Which statement describes AWS pay-as-you-go pricing?

- A. You pay only for the services you use, for as long as you use them, without long-term contracts or upfront commitments.
- B. You pay a fixed monthly fee sized to your expected peak usage.
- C. You must prepay for one year of capacity before you can launch resources.
- D. You pay for the full capacity of the physical servers your resources run on, whether or not you use it.

> [!success]- Answer
> **A.** Pay-as-you-go means paying for what you consume, when you consume it, with no contract required.
> - B: A fixed fee sized to peak is the on-premises model that pay-as-you-go replaces.
> - C: Prepayment is optional (for example, Reserved Instances); it is never required to start.
> - D: You pay for the resources you use, not for whole physical servers (unless you choose an option such as Dedicated Hosts).
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q4
When a customer payment fails, an application must immediately send one message that reaches the finance team by email and by SMS text message and also triggers an AWS Lambda function. Which service should deliver this message to all of these subscribers?

- A. Amazon Simple Queue Service (Amazon SQS)
- B. Amazon Simple Email Service (Amazon SES)
- C. Amazon Simple Notification Service (Amazon SNS)
- D. AWS Step Functions

> [!success]- Answer
> **C.** SNS is a publish/subscribe service: one message published to a topic is pushed to every subscriber, including email addresses, SMS numbers, and Lambda functions.
> - A: SQS holds messages in a queue for one consumer to poll; it does not push one message to email, SMS, and Lambda at once.
> - B: SES sends email, but not SMS messages or Lambda invocations.
> - D: Step Functions orchestrates the steps of a workflow; it is not a notification service.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q5
Under the AWS shared responsibility model, for which service does the customer take on the most security responsibility?

- A. Amazon EC2
- B. Amazon RDS
- C. AWS Lambda
- D. Amazon DynamoDB

> [!success]- Answer
> **A.** EC2 is infrastructure as a service: the customer manages the guest operating system, its patches, installed software, and firewall configuration on top of what AWS provides.
> - B: With RDS, AWS manages the operating system and database software patching.
> - C: With Lambda, AWS manages the servers, operating system, and runtime environment.
> - D: DynamoDB is fully managed; the customer manages only its data and access.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q6
A finance manager wants to see a graph of the company's AWS costs by service for the past several months, filter it by linked account, and view a forecast of the coming months. She does not need to set any thresholds or alerts. Which tool should she use?

- A. AWS Budgets
- B. AWS Pricing Calculator
- C. AWS Cost and Usage Report
- D. AWS Cost Explorer

> [!success]- Answer
> **D.** Cost Explorer visualizes cost and usage over time, with filters and grouping (by service, account, tag, and more), and forecasts future spend.
> - A: Budgets is for setting thresholds and alerts, which she does not need.
> - B: Pricing Calculator estimates the cost of planned resources; it does not show actual past costs.
> - C: The Cost and Usage Report is a detailed data file delivered to S3, not an interactive graph.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q7
During a Well-Architected review, a team confirms that its account's service quotas leave enough headroom for a failover that doubles its instance count, and that its network has enough IP addresses for growth and redundant connectivity to its data center. Which pillar of the AWS Well-Architected Framework do these foundations belong to?

- A. Performance efficiency
- B. Reliability
- C. Operational excellence
- D. Security

> [!success]- Answer
> **B.** Managing service quotas and planning network topology are the foundations of the Reliability pillar, which makes sure a workload can perform its function consistently and recover from failure.
> - A: Performance efficiency is about choosing and using resources efficiently to meet performance requirements.
> - C: Operational excellence is about running and improving operations, such as operations as code and learning from events.
> - D: Security is about protecting data, systems, and assets.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q8
A company runs a production Amazon RDS for PostgreSQL database in one Availability Zone. If that Availability Zone fails, the database must fail over automatically to a synchronously replicated standby in another Availability Zone, without the application changing its connection endpoint. What should the company use?

- A. A read replica in the same Availability Zone
- B. A larger DB instance class
- C. An RDS Multi-AZ deployment
- D. Manual snapshots copied to another Region

> [!success]- Answer
> **C.** A Multi-AZ deployment keeps a synchronous standby in a different Availability Zone and fails over to it automatically, keeping the same endpoint.
> - A: A read replica is updated asynchronously and is used to scale reads; one in the same Availability Zone also fails with it.
> - B: A larger instance adds capacity, not a standby.
> - D: Restoring snapshots is a manual recovery that takes time; it is not automatic failover.
>
> Review: [[3.4 Database Services]]

### Q9
An administrator creates a new security group in a VPC and adds no rules to it. What traffic does the security group allow?

- A. No inbound traffic and all outbound traffic
- B. All inbound traffic and no outbound traffic
- C. All inbound and outbound traffic within the same subnet
- D. No inbound traffic and no outbound traffic

> [!success]- Answer
> **A.** A new security group has no inbound rules, so all inbound traffic is blocked, and it includes a default outbound rule that allows all outbound traffic.
> - B: Inbound traffic is never allowed until you add an allow rule.
> - C: Security groups do not allow traffic based on being in the same subnet.
> - D: A new security group comes with an outbound rule that allows all outbound traffic.
>
> Review: [[2.4 Security Components and Resources]]

### Q10
A company stores customer data in S3 Standard in a bucket in the Europe (Frankfurt) Region and configures nothing else. Where is the data stored?

- A. Copied to every AWS Region for durability
- B. At the edge locations nearest to the users who read it
- C. In the US East (N. Virginia) Region, where Amazon S3 is managed
- D. Only in the Frankfurt Region, across multiple Availability Zones, unless the company sets up replication to another Region

> [!success]- Answer
> **D.** Data stays in the Region you choose; AWS does not move it to another Region unless you configure that, such as with S3 Cross-Region Replication. S3 Standard stores it redundantly across Availability Zones within that Region.
> - A: AWS does not copy data to other Regions on its own; this is why Region choice supports data sovereignty.
> - B: Edge locations cache content only when you use a service such as CloudFront; they are not where S3 stores data.
> - C: Each S3 bucket lives in the Region where it was created.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q11
A CFO asks how moving from company-owned servers to AWS will change the company's spending model. Which statement is correct?

- A. Spending shifts from operational expenditure to capital expenditure.
- B. Upfront capital spending on hardware is replaced by variable operational spending based on actual usage.
- C. All AWS charges become fixed monthly fees regardless of usage.
- D. The company must depreciate its AWS resources over their useful life.

> [!success]- Answer
> **B.** On AWS the company stops buying hardware up front (capital expenditure) and instead pays for what it uses as an operating expense that varies with usage.
> - A: This is backwards; the move is from capital to operational expenditure.
> - C: Most AWS charges vary with usage.
> - D: The company does not own AWS hardware, so it has nothing to depreciate.
>
> Review: [[1.4 Cloud Economics]]

### Q12
A security review finds that the root user of the company's AWS account has an active access key, which a nightly script uses. Following AWS best practices, what should the company do?

- A. Rotate the root user access key every 90 days
- B. Store the root user access key in AWS Secrets Manager
- C. Give the script an IAM role or IAM identity with only the permissions it needs, then delete the root user access key
- D. Enable MFA on the root user and keep the access key

> [!success]- Answer
> **C.** AWS recommends that the root user have no access keys. Automation should use an IAM identity limited to what it needs, and the root access key should be deleted.
> - A: Rotating the key still leaves unrestricted, long-term root credentials in use.
> - B: Storing the key more safely does not remove the risk of the root user having an access key at all.
> - D: MFA protects console sign-in, but the access key would still give full programmatic access to the account.
>
> Review: [[2.3 Access Management and IAM]]

### Q13
A team will run a six-week pilot on Amazon EC2. Its usage is unpredictable, the instances cannot be interrupted, it will make no commitment beyond the pilot, and it needs no capacity guarantee. Which purchasing option is most cost-effective?

- A. On-Demand Instances
- B. Spot Instances
- C. 1-year Standard Reserved Instances
- D. Dedicated Hosts

> [!success]- Answer
> **A.** On-Demand Instances need no commitment and are not interrupted, which suits short, unpredictable workloads.
> - B: Spot Instances can be interrupted when AWS needs the capacity back.
> - C: A 1-year term far outlasts a six-week pilot.
> - D: Dedicated Hosts cost more and are for licensing or compliance needs this pilot does not have.
>
> Review: [[4.1 AWS Pricing Models]]

### Q14
A company stores product images and videos in an S3 bucket in one Region. Users on other continents report slow load times. The company wants copies of the content cached at locations near its users and less load on the bucket. Which service should it use?

- A. AWS Global Accelerator
- B. Amazon Route 53
- C. AWS Direct Connect
- D. Amazon CloudFront

> [!success]- Answer
> **D.** CloudFront is a content delivery network that caches content at edge locations close to viewers, lowering latency and reducing requests to the origin bucket.
> - A: Global Accelerator routes traffic over the AWS network to an endpoint but does not cache content.
> - B: Route 53 answers DNS queries; it does not cache or deliver content.
> - C: Direct Connect is a private link from a data center to AWS, not a way to serve public users.
>
> Review: [[3.5 Network Services]]

### Q15
An administrator wants to trim an IAM role's permissions to least privilege. She needs to see which AWS services the role has actually used and when it last used each one. Which IAM feature provides this?

- A. IAM credential report
- B. IAM last accessed information (access advisor)
- C. AWS Artifact reports
- D. Amazon CloudWatch metrics

> [!success]- Answer
> **B.** Last accessed information shows which services an IAM identity's permissions allow and when each was last used, so unused permissions can be removed.
> - A: The credential report lists IAM users and the status of their passwords, access keys, and MFA, not the services a role used.
> - C: Artifact holds AWS's compliance reports, not data about the customer's identities.
> - D: CloudWatch metrics measure resource performance; they do not track permission use.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q16
A company's CEO and COO want to make sure cloud investments accelerate the company's digital transformation and business outcomes. The work includes strategy management, innovation management, product management, and finding new ways to monetize the company's data. Which AWS Cloud Adoption Framework (AWS CAF) perspective covers these capabilities?

- A. Governance
- B. People
- C. Business
- D. Operations

> [!success]- Answer
> **C.** The Business perspective makes sure cloud investments accelerate business outcomes. Its capabilities include strategy, innovation, and product management and data monetization.
> - A: Governance covers program management, risk management, and cloud financial management.
> - B: People covers culture, organizational structure, leadership, and workforce skills.
> - D: Operations covers delivering cloud services day to day: observability, incident management, and patching.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q17
A database runs on a single Amazon EC2 instance. It needs block storage whose data persists when the instance is stopped and started, and that can be backed up with point-in-time snapshots. Which storage should it use?

- A. Amazon Elastic Block Store (Amazon EBS)
- B. EC2 instance store
- C. Amazon Elastic File System (Amazon EFS)
- D. S3 Glacier Flexible Retrieval

> [!success]- Answer
> **A.** EBS provides persistent block storage volumes for EC2 that exist independently of the instance's running state and support point-in-time snapshots.
> - B: Instance store is temporary; its data is lost when the instance stops.
> - C: EFS is a shared file system, not block storage for a single instance's database volume.
> - D: Glacier Flexible Retrieval is archive object storage, not a volume an instance can use.
>
> Review: [[3.6 Storage Services]]

### Q18
An IAM user belongs to two IAM groups. One group's policy allows `s3:DeleteObject` on a bucket. The other group's policy explicitly denies `s3:DeleteObject` on the same bucket. What happens when the user tries to delete an object in that bucket?

- A. The request is allowed, because any allow grants access.
- B. The request is allowed, because group policies are evaluated in alphabetical order.
- C. The result depends on which group the user joined first.
- D. The request is denied, because an explicit deny overrides any allow.

> [!success]- Answer
> **D.** In IAM policy evaluation, an explicit deny in any applicable policy always wins over an allow.
> - A: An allow grants access only when no explicit deny applies.
> - B: Policy evaluation does not depend on group names or order.
> - C: The order in which the user joined groups does not matter.
>
> Review: [[2.3 Access Management and IAM]]

### Q19
Every night, an administrator must run the same set of commands that stop all development EC2 instances. The commands run from a scheduled shell script on a Linux server. Which way of accessing AWS fits this need?

- A. AWS Management Console
- B. AWS CloudShell
- C. AWS CLI
- D. AWS Cloud9

> [!success]- Answer
> **C.** The AWS CLI runs AWS commands from a command-line shell, so a scheduled script can repeat them automatically.
> - A: The console is a web interface for a person clicking through tasks, not for scheduled automation.
> - B: CloudShell is an interactive shell in the browser, not something a server's scheduled script runs on.
> - D: Cloud9 is a browser-based IDE for writing code, not a scheduler for server scripts.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q20
Which TWO are design principles of the Performance efficiency pillar of the AWS Well-Architected Framework? (Select TWO.)

- A. Implement a strong identity foundation
- B. Democratize advanced technologies
- C. Manage change in automation
- D. Consider mechanical sympathy
- E. Adopt a consumption model

> [!success]- Answer
> **B and D.** Democratizing advanced technologies (consuming complex technology as a service) and mechanical sympathy (choosing the technology that best fits how you use it) are Performance efficiency principles.
> - A: A strong identity foundation is a Security principle.
> - C: Managing change in automation is a Reliability principle.
> - E: Adopting a consumption model is a Cost optimization principle.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q21
A company on the Basic Support plan sees a charge on its AWS bill that it does not recognize and wants AWS to explain it. What can the company do?

- A. Nothing; help with billing questions requires the Developer plan or higher.
- B. Open an account and billing case in the AWS Support Center, because customer service for account and billing questions is included with Basic Support.
- C. Contact its Technical Account Manager.
- D. Report the charge to the AWS Trust and Safety team.

> [!success]- Answer
> **B.** Every AWS account, including those on Basic Support, has access to customer service for account and billing questions through the Support Center.
> - A: Paid plans add technical support; billing and account help is included for all customers.
> - C: Technical Account Managers come only with Enterprise On-Ramp (a pool) and Enterprise (designated).
> - D: Trust and Safety handles reports of abuse from AWS resources, not billing questions.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q22
Under the AWS shared responsibility model, which TWO tasks are AWS's responsibility? (Select TWO.)

- A. Patching the operating system that AWS Lambda functions run on
- B. Setting the IAM account password policy
- C. Maintaining the physical hardware behind Amazon EBS volumes
- D. Configuring network ACLs for a VPC subnet
- E. Encrypting data on the client before uploading it to Amazon S3

> [!success]- Answer
> **A and C.** AWS patches the operating system that Lambda uses and maintains all physical hardware.
> - B: Setting password policies is a customer responsibility.
> - D: Configuring networks and firewalls, including network ACLs, is a customer responsibility.
> - E: Client-side encryption and data integrity are customer responsibilities.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q23
A social media app must automatically detect inappropriate content and identify objects and scenes in the photos and videos users upload. The company does not want to build machine learning models. Which service should it use?

- A. Amazon Textract
- B. Amazon Comprehend
- C. Amazon Kendra
- D. Amazon Rekognition

> [!success]- Answer
> **D.** Rekognition identifies objects, people, text, scenes, activities, and inappropriate content in images and videos, with no ML experience needed.
> - A: Textract extracts text and data from scanned documents.
> - B: Comprehend analyzes text for sentiment, key phrases, and entities, not images.
> - C: Kendra is an intelligent search service for documents.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q24
Most of a company's EC2 instances run below 10% CPU utilization. The company plans to buy 3-year Savings Plans to cut costs. To get the largest savings, what should it do first?

- A. Rightsize the instances to smaller types, then base the commitment on the reduced usage
- B. Buy the Savings Plans for current usage, then rightsize
- C. Move the instances to Dedicated Hosts
- D. Raise the minimum size of its Auto Scaling groups

> [!success]- Answer
> **A.** Rightsizing first means the commitment covers only the capacity actually needed, so the company does not lock in waste for three years.
> - B: Committing first sets the hourly commitment at the oversized level; after rightsizing, part of it would go unused but still be paid for.
> - C: Dedicated Hosts cost more and do not address oversizing.
> - D: A higher minimum adds capacity the workload does not need.
>
> Review: [[1.4 Cloud Economics]]

### Q25
A company wants continuous threat detection that analyzes AWS CloudTrail events, VPC Flow Logs, and DNS logs to find activity such as compromised instances or unusual API calls. It does not want to deploy agents or security software to get started. Which service should it use?

- A. Amazon Inspector
- B. AWS Trusted Advisor
- C. Amazon GuardDuty
- D. AWS Artifact

> [!success]- Answer
> **C.** GuardDuty is an intelligent threat detection service that continuously analyzes CloudTrail, VPC Flow Logs, and DNS logs, and is enabled with no agents to deploy.
> - A: Inspector scans workloads for software vulnerabilities and network exposure, not live threats in log data.
> - B: Trusted Advisor checks configurations against best practices; it does not detect active threats.
> - D: Artifact provides AWS's compliance reports.
>
> Review: [[2.4 Security Components and Resources]]

### Q26
Which TWO are benefits that AWS edge locations provide? (Select TWO.)

- A. Caching copies of content close to viewers so that responses arrive with lower latency
- B. Hosting the primary copy of Amazon RDS databases
- C. Running the customer's EC2 instances in every major city
- D. Replacing Availability Zones as the way to achieve high availability
- E. Giving user traffic an entry point near the user onto the AWS global network, as AWS Global Accelerator does

> [!success]- Answer
> **A and E.** Edge locations cache content for Amazon CloudFront and give traffic an on-ramp to the AWS global network for services such as Global Accelerator, both of which reduce latency.
> - B: RDS databases run in Availability Zones within a Region, not at edge locations.
> - C: Edge locations do not host customers' EC2 instances.
> - D: High availability for workloads comes from multiple Availability Zones; edge locations do not replace them.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q27
A company replaces its self-hosted, on-premises customer relationship management (CRM) application with a software as a service (SaaS) CRM product and moves its customer data into the new product. Which migration strategy is this?

- A. Rehost
- B. Repurchase
- C. Refactor
- D. Retire

> [!success]- Answer
> **B.** Repurchase means moving to a different product, typically a SaaS offering, instead of migrating the existing application.
> - A: Rehost moves the existing application to AWS without changes.
> - C: Refactor re-architects the existing application, often to cloud-native services.
> - D: Retire means decommissioning an application that is no longer needed; here the business function continues in a new product.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q28
A company will commit to EC2 Reserved Instances for three years for a steady workload. It expects to need different instance families as its application changes and wants to exchange the reservation for other instance configurations during the term. Which option should it choose?

- A. Standard Reserved Instances
- B. Spot Instances
- C. Dedicated Hosts
- D. Convertible Reserved Instances

> [!success]- Answer
> **D.** Convertible Reserved Instances can be exchanged for Reserved Instances with different attributes, such as instance family, during the term, in return for a smaller discount than Standard RIs.
> - A: Standard Reserved Instances give the largest RI discount but cannot be exchanged for a different instance family.
> - B: Spot Instances are not a commitment and can be interrupted.
> - C: Dedicated Hosts are physical servers for licensing and compliance needs, not a flexible discount.
>
> Review: [[4.1 AWS Pricing Models]]

### Q29
Each time an image is uploaded to an S3 bucket, a company wants code to create a thumbnail. Each run takes a few seconds, uploads arrive unpredictably, and the company wants no servers to manage and to pay only when the code runs. Which service should it use?

- A. AWS Lambda
- B. An Amazon EC2 Auto Scaling group
- C. Amazon Lightsail
- D. Amazon ECS on the EC2 launch type

> [!success]- Answer
> **A.** Lambda runs code in response to events such as S3 uploads, with no servers to manage, and charges only for requests and the time the code runs.
> - B: EC2 instances must be managed and are billed while they run, even when idle between uploads.
> - C: Lightsail provides virtual servers billed monthly.
> - D: The EC2 launch type requires managing the cluster's EC2 instances.
>
> Review: [[3.3 Compute Services]]

### Q30
A company serves its website through Amazon CloudFront. Under the shared responsibility model, which task is AWS's responsibility?

- A. Choosing whether viewers must connect over HTTPS
- B. Setting the bucket policy on the S3 origin
- C. Physical security and operation of the edge locations that serve the content
- D. Configuring geographic restrictions on the distribution

> [!success]- Answer
> **C.** Edge location management, including physical security, is AWS's responsibility.
> - A: Choosing the viewer protocol policy is the customer's configuration.
> - B: Access to the customer's S3 bucket is the customer's responsibility.
> - D: Geographic restrictions are a setting the customer chooses.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q31
Which statement about subnets in an Amazon VPC is correct?

- A. A subnet can span all Availability Zones in a Region.
- B. Each subnet resides entirely within one Availability Zone.
- C. A subnet can span multiple Regions.
- D. Subnets are created in edge locations.

> [!success]- Answer
> **B.** A VPC spans all Availability Zones in its Region, but each subnet sits entirely within one Availability Zone. To use several Availability Zones, you create a subnet in each.
> - A: A subnet cannot span Availability Zones.
> - C: A VPC, and therefore its subnets, exists within a single Region.
> - D: Subnets exist in Availability Zones, not edge locations.
>
> Review: [[3.5 Network Services]]

### Q32
A small company adds speech recognition, data analytics, and IoT features to its product within weeks by using AWS services, instead of building and running that technology itself. Which benefit of the AWS Cloud does this describe?

- A. Economies of scale
- B. High availability
- C. Elasticity
- D. Agility

> [!success]- Answer
> **D.** Agility includes access to a broad range of technologies that teams can adopt quickly, so they innovate faster.
> - A: Economies of scale explain AWS's lower prices.
> - B: High availability is about staying accessible during failures.
> - C: Elasticity is scaling capacity up and down with demand.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q33
An operations team wants to receive an email whenever the average CPU utilization of an EC2 instance stays above 80% for 15 minutes. Which service should it use?

- A. Amazon CloudWatch alarms
- B. AWS CloudTrail
- C. AWS Config
- D. AWS X-Ray

> [!success]- Answer
> **A.** CloudWatch collects metrics such as CPU utilization, and a CloudWatch alarm can watch a metric against a threshold over a period and send a notification through Amazon SNS.
> - B: CloudTrail records API calls, not performance metrics.
> - C: Config records and evaluates resource configurations, not CPU utilization.
> - D: X-Ray traces requests through an application.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q34
A development team wants one managed service that compiles source code, runs unit tests, and produces packages ready to deploy, and another that automates deploying those packages to EC2 instances and on-premises servers. Which TWO services should it use? (Select TWO.)

- A. AWS CodeArtifact
- B. AWS CodeBuild
- C. AWS CodeDeploy
- D. AWS X-Ray
- E. AWS AppConfig

> [!success]- Answer
> **B and C.** CodeBuild compiles code, runs tests, and produces artifacts, and CodeDeploy automates application deployments to EC2, on-premises servers, and other compute services.
> - A: CodeArtifact stores and shares software packages; it does not build or deploy.
> - D: X-Ray traces requests to find performance problems.
> - E: AppConfig deploys application configuration changes, not application packages.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q35
Finance requires every resource to carry a CostCenter tag. An administrator must find all resources that are missing the tag across several Regions and add it to many resources at once. Which service should the administrator use?

- A. AWS Cost Explorer
- B. AWS Budgets
- C. AWS Resource Groups and Tag Editor
- D. AWS Billing Conductor

> [!success]- Answer
> **C.** Tag Editor searches for resources across Regions and adds, edits, or removes tags on many resources at once.
> - A: Cost Explorer analyzes costs and can group by tag, but it does not apply tags.
> - B: Budgets alerts on spending thresholds.
> - D: Billing Conductor produces pro forma bills with custom rates.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q36
Which is a supported multi-factor authentication (MFA) method for an IAM user signing in to the AWS Management Console?

- A. A second, longer password
- B. A FIDO security key or passkey
- C. The user's access key ID
- D. A security question chosen by the administrator

> [!success]- Answer
> **B.** IAM supports FIDO security keys and passkeys, virtual authenticator apps, and hardware TOTP tokens as MFA methods.
> - A: A second password is the same factor (something you know), so it is not multi-factor.
> - C: An access key ID is for programmatic access and is not an MFA device.
> - D: Security questions are not an IAM MFA method.
>
> Review: [[2.3 Access Management and IAM]]

### Q37
A company stops its development and test environments every evening and weekend, so it pays only for the hours they are used and cuts their cost by about 75%. Which AWS Well-Architected design principle is it applying?

- A. Stop guessing capacity
- B. Experiment more often
- C. Scale horizontally to increase aggregate workload availability
- D. Adopt a consumption model

> [!success]- Answer
> **D.** Adopt a consumption model is a Cost optimization principle: pay only for the computing resources you consume, for example by stopping non-production environments when not in use.
> - A: Stop guessing capacity is a Reliability principle about scaling to demand.
> - B: Experiment more often is a Performance efficiency principle.
> - C: Scaling horizontally is a Reliability principle about availability.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q38
A company archives project files that it reads once or twice a year. When files are requested, some are needed within minutes and others can arrive in bulk within hours. Millisecond access is not needed. Which S3 storage class meets these needs at the lowest cost?

- A. S3 Standard-IA
- B. S3 Glacier Deep Archive
- C. S3 Glacier Flexible Retrieval
- D. S3 Standard

> [!success]- Answer
> **C.** Glacier Flexible Retrieval is low-cost archive storage with expedited retrievals in 1–5 minutes and standard and bulk retrievals in hours.
> - A: Standard-IA offers millisecond access, which is not needed, at a higher storage price.
> - B: Deep Archive is cheaper but has no expedited option; its fastest retrieval takes up to 12 hours.
> - D: S3 Standard is for frequently accessed data and costs the most to store.
>
> Review: [[3.6 Storage Services]]

### Q39
A company stores sensitive files in Amazon S3 and must protect them both at rest and in transit. Which TWO actions meet these requirements? (Select TWO.)

- A. Enable S3 Versioning on the bucket
- B. Turn on S3 Transfer Acceleration
- C. Enable server-side encryption with AWS KMS keys on the bucket
- D. Run Amazon Macie on the bucket
- E. Add a bucket policy that denies requests not made over HTTPS (TLS)

> [!success]- Answer
> **C and E.** Server-side encryption with KMS keys protects the objects at rest, and requiring HTTPS protects them in transit.
> - A: Versioning keeps previous versions of objects; it does not encrypt them.
> - B: Transfer Acceleration speeds up long-distance uploads; it is not an encryption control.
> - D: Macie finds sensitive data; it does not encrypt it.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q40
A company runs all its workloads in its own data center, using virtualization and resource management software it operates itself, and offers self-service provisioning to internal teams. Nothing runs in a public cloud. Which deployment model is this?

- A. On-premises (private cloud)
- B. Hybrid
- C. Cloud
- D. Multi-Region

> [!success]- Answer
> **A.** An on-premises or private cloud deployment uses virtualization and resource management tools in the company's own data center.
> - B: Hybrid connects on-premises infrastructure with cloud resources, and this company uses no cloud.
> - C: A cloud deployment runs workloads in a public cloud such as AWS.
> - D: Multi-Region describes spreading a cloud workload across AWS Regions.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q41
A company owns licenses for a commercial database, and the license terms allow use in the cloud. When it moves the database to Amazon EC2, which approach avoids paying for the database license a second time?

- A. Launch from a license-included AMI
- B. Bring Your Own License (BYOL)
- C. Subscribe to the database through AWS Marketplace with pay-as-you-go pricing
- D. Run the database on Spot Instances

> [!success]- Answer
> **B.** BYOL reuses licenses the company already owns, so it pays AWS only for the infrastructure.
> - A: License-included pricing adds the license cost to the hourly price, so the company would pay for a license it already has.
> - C: A Marketplace pay-as-you-go subscription also includes a license charge.
> - D: Spot is a purchasing option for compute, not a licensing model, and can interrupt a database.
>
> Review: [[1.4 Cloud Economics]]

### Q42
An administrator receives an Access Denied error from Amazon S3. She wants AWS-written articles that answer the questions customers most often ask AWS Support, with step-by-step resolutions. Which resource should she use?

- A. AWS Security Blog
- B. AWS Artifact
- C. AWS Trust and Safety team
- D. AWS Knowledge Center

> [!success]- Answer
> **D.** The AWS Knowledge Center (part of AWS re:Post) contains AWS-written articles and videos that answer the most frequent questions and requests AWS receives from customers.
> - A: The Security Blog announces security features and discusses best practices; it is not a library of answers to common support issues.
> - B: Artifact provides compliance reports and agreements.
> - C: Trust and Safety handles reports of abuse of AWS resources.
>
> Review: [[2.4 Security Components and Resources]]

### Q43
A migration team wants time-tested strategies, guides, and step-by-step patterns, written by AWS and AWS Partners, for migrating and modernizing workloads. Which resource should it use?

- A. AWS re:Post
- B. AWS Trusted Advisor
- C. AWS Prescriptive Guidance
- D. AWS Health Dashboard

> [!success]- Answer
> **C.** AWS Prescriptive Guidance provides time-tested strategies, guides, and patterns from AWS and AWS Partners for migration, modernization, and optimization projects.
> - A: re:Post is a community question-and-answer service, not a curated library of migration patterns.
> - B: Trusted Advisor checks an account against best practices.
> - D: The Health Dashboard shows AWS service health and events affecting your account.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q44
A company is setting up an AWS Site-to-Site VPN connection between its data center and one VPC. Which TWO components form the two ends of the VPN connection? (Select TWO.)

- A. A virtual private gateway
- B. An internet gateway
- C. A NAT gateway
- D. A customer gateway
- E. A Direct Connect gateway

> [!success]- Answer
> **A and D.** The virtual private gateway is the VPN endpoint on the AWS side, and the customer gateway is the physical or software appliance the customer manages on premises.
> - B: An internet gateway connects a VPC to the internet; it is not a VPN endpoint.
> - C: A NAT gateway lets private instances reach the internet.
> - E: A Direct Connect gateway is used with Direct Connect to reach VPCs in multiple Regions.
>
> Review: [[3.5 Network Services]]

### Q45
An API built on AWS Lambda and Amazon DynamoDB on-demand capacity handles a few requests per minute overnight and thousands per second during a product launch. Nobody plans capacity in advance, and costs fall back when traffic drops. Which benefit of the AWS Cloud does this demonstrate?

- A. Elasticity
- B. Agility
- C. Global reach
- D. Economies of scale

> [!success]- Answer
> **A.** Elasticity is capacity that grows and shrinks automatically with demand, so you pay for what you use. Serverless services provide it with no capacity planning.
> - B: Agility is getting resources and new technologies quickly to innovate.
> - C: Global reach is deploying in many geographic locations.
> - D: Economies of scale explain AWS's lower prices.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q46
Under the AWS shared responsibility model, AWS is responsible for "security of the cloud." What does this cover?

- A. Customer data and its encryption
- B. The hardware, software, networking, and facilities that run AWS Cloud services
- C. IAM users and permissions in customer accounts
- D. The guest operating systems and applications that customers run on EC2

> [!success]- Answer
> **B.** Security of the cloud is protecting the infrastructure that runs all AWS services: hardware, software, networking, and facilities, including Regions, Availability Zones, and edge locations.
> - A: Customer data is part of security in the cloud, the customer's responsibility.
> - C: Identity and access management is the customer's responsibility.
> - D: Guest operating systems and applications on EC2 are the customer's responsibility.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q47
Which workload is the best fit for object storage such as Amazon S3?

- A. The boot volume of an EC2 instance
- B. A shared file system that many Linux servers mount at the same time
- C. Low-latency block storage for a transactional database's data files
- D. Millions of images, backups, and data lake files accessed over HTTPS through an API

> [!success]- Answer
> **D.** Object storage keeps data as objects in buckets, accessed through an API over HTTP(S), and scales to virtually unlimited amounts of unstructured data such as media, backups, and data lakes.
> - A: Boot volumes use block storage (Amazon EBS).
> - B: A shared mounted file system is file storage (Amazon EFS or Amazon FSx).
> - C: Database data files need block storage such as EBS.
>
> Review: [[3.6 Storage Services]]

### Q48
A company wants its Windows EC2 instances to join a Microsoft Active Directory domain in AWS. It wants an actual Microsoft Active Directory that AWS manages, including patching and replication, instead of running domain controllers itself. Which service should it use?

- A. Amazon Cognito
- B. AWS IAM Identity Center (AWS Single Sign-On)
- C. AWS Directory Service (AWS Managed Microsoft AD)
- D. AWS Resource Access Manager (AWS RAM)

> [!success]- Answer
> **C.** AWS Directory Service provides managed Microsoft Active Directory in AWS, so instances and applications can use a real AD domain without the company running domain controllers.
> - A: Cognito handles sign-up and sign-in for customers of web and mobile apps; it is not an AD domain.
> - B: IAM Identity Center provides workforce single sign-on to AWS accounts and applications; it can connect to AD but does not host an AD domain for instances to join.
> - D: AWS RAM shares AWS resources between accounts.
>
> Review: [[2.3 Access Management and IAM]]

### Q49
Before migrating 400 servers, a company wants to collect configuration, utilization, and dependency data from its on-premises servers to plan the migration. During the migration, it wants to track the progress of each application in one central place, across the tools it uses. Which TWO services meet these needs? (Select TWO.)

- A. AWS Database Migration Service (AWS DMS)
- B. AWS Application Discovery Service
- C. AWS Elastic Disaster Recovery
- D. AWS Transfer Family
- E. AWS Migration Hub

> [!success]- Answer
> **B and E.** Application Discovery Service collects usage and configuration data about on-premises servers to plan a migration, and Migration Hub is the central place to discover servers, plan, and track each application's migration status.
> - A: DMS migrates databases; it does not inventory servers or track overall progress.
> - C: Elastic Disaster Recovery replicates servers for recovery, not migration planning.
> - D: Transfer Family moves files into and out of AWS storage over protocols such as SFTP.
>
> Current status: AWS Application Discovery Service and AWS Migration Hub closed to new customers on November 7, 2025; AWS recommends AWS Transform for new projects. The exam still tests both services.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q50
A bank wants a chatbot on its website that understands customers' typed and spoken questions. It also wants its mobile app to read account alerts aloud in a natural-sounding voice. Which TWO services should it use? (Select TWO.)

- A. Amazon Translate
- B. Amazon Comprehend
- C. Amazon Lex
- D. Amazon Polly
- E. Amazon Textract

> [!success]- Answer
> **C and D.** Lex builds conversational interfaces that use voice and text, and Polly converts text into lifelike speech.
> - A: Translate converts text between languages.
> - B: Comprehend extracts sentiment, key phrases, and entities from text; it does not hold conversations.
> - E: Textract extracts text and data from scanned documents.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q51
Which TWO factors affect a company's monthly bill for Amazon S3? (Select TWO.)

- A. The amount of data stored and the storage class it is stored in
- B. The number and type of requests, such as PUT and GET
- C. Data transferred into S3 from the internet
- D. The number of IAM users who can access the bucket
- E. The number of Availability Zones that S3 Standard stores data across

> [!success]- Answer
> **A and B.** S3 charges for storage (per GB, at a price set by the storage class) and for requests; data transfer out and retrievals from some classes also add charges.
> - C: Data transferred in from the internet is free.
> - D: IAM users and permissions have no S3 charge.
> - E: S3 Standard's redundancy across Availability Zones is included in its storage price; you do not choose or pay per Availability Zone.
>
> Review: [[4.1 AWS Pricing Models]]

### Q52
A security team needs records of the IP traffic that was accepted and rejected going to and from the network interfaces in its VPC, to use in investigations. Which feature provides this?

- A. VPC Flow Logs
- B. AWS CloudTrail
- C. AWS Config
- D. AWS X-Ray

> [!success]- Answer
> **A.** VPC Flow Logs capture information about IP traffic to and from network interfaces in a VPC, including whether it was accepted or rejected.
> - B: CloudTrail records API calls, not network traffic.
> - C: Config records resource configurations and their changes.
> - D: X-Ray traces application requests for performance analysis.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q53
A company is migrating an on-premises PostgreSQL database to Amazon RDS for PostgreSQL with minimal downtime. Which statement is correct?

- A. It must first convert the schema with the AWS Schema Conversion Tool (AWS SCT).
- B. AWS DMS can migrate the data with ongoing replication, and no schema conversion is needed because the source and target engines are the same.
- C. It must ship the data on AWS Snowball Edge devices.
- D. It must rehost the database server with AWS Application Migration Service.

> [!success]- Answer
> **B.** This is a homogeneous migration (same engine). AWS DMS moves the data and keeps the source in sync with ongoing replication; schema conversion is only needed when the engines differ.
> - A: SCT is for heterogeneous migrations, such as Oracle to PostgreSQL.
> - C: Snowball Edge is for large offline transfers, and nothing in the stem requires one.
> - D: Application Migration Service rehosts whole servers onto EC2; it cannot move a database into Amazon RDS.
>
> Review: [[3.4 Database Services]]

### Q54
A company has identified and prioritized its cloud transformation opportunities and the capability gaps it must close. It is now delivering pilot initiatives in production and demonstrating incremental business value. Which AWS CAF transformation phase is it in?

- A. Envision
- B. Align
- C. Scale
- D. Launch

> [!success]- Answer
> **D.** The Launch phase delivers pilot initiatives in production and demonstrates incremental business value.
> - A: Envision identifies and prioritizes transformation opportunities.
> - B: Align identifies capability gaps and dependencies and builds strategies to close them.
> - C: Scale expands the production pilots and business value to the desired scale.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q55
A company is deciding whether to run Microsoft SQL Server on Amazon EC2 or on Amazon RDS for SQL Server. Which task is the company's responsibility on EC2 but AWS's responsibility on RDS?

- A. Installing database software patches
- B. Managing database logins and permissions
- C. Configuring security groups that control access to the database
- D. Physical security of the data center

> [!success]- Answer
> **A.** On EC2 the customer installs and patches the database software. On RDS, AWS patches the database engine and the operating system as part of the managed service.
> - B: Database logins and permissions are the customer's responsibility on both.
> - C: Network access configuration is the customer's responsibility on both.
> - D: Physical security is AWS's responsibility on both.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q56
A small business owner with little AWS experience wants to launch a simple WordPress website on a virtual server for a predictable, low monthly price that bundles compute, storage, and data transfer. Which service should she use?

- A. AWS Elastic Beanstalk
- B. EC2 Dedicated Instances
- C. Amazon Lightsail
- D. AWS Batch

> [!success]- Answer
> **C.** Lightsail launches simple projects, such as WordPress sites, from a simple interface with bundled monthly plans that include compute, storage, and a data transfer allowance.
> - A: Elastic Beanstalk deploys applications on EC2 and other resources billed separately; it has no bundled monthly price.
> - B: Dedicated Instances run on single-tenant hardware at a higher price, which a small website does not need.
> - D: AWS Batch runs batch computing jobs.
>
> Review: [[3.3 Compute Services]]

### Q57
Before every major release, a team holds "pre-mortem" exercises to work out how the release could fail and then removes or mitigates those risks. After each operational event, it updates its runbooks and procedures. Which Well-Architected Framework pillar do these practices represent?

- A. Reliability
- B. Operational excellence
- C. Security
- D. Performance efficiency

> [!success]- Answer
> **B.** Anticipating failure through pre-mortems and refining operations procedures frequently are Operational excellence design principles.
> - A: Reliability is about the workload itself recovering from failure, scaling, and managing quotas, not the team's release and runbook practices.
> - C: Security is about protecting data, systems, and assets.
> - D: Performance efficiency is about using resources efficiently.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q58
A company wants a standby copy of its database that is kept synchronously up to date, so that a failover loses no committed data, and that protects against the failure of a single data center. Where should the standby be placed for the lowest replication latency?

- A. In a different AWS Region
- B. At an edge location
- C. In an AWS Wavelength Zone
- D. In a different Availability Zone in the same Region

> [!success]- Answer
> **D.** Availability Zones in a Region are physically separate, do not share single points of failure, and are linked by high-bandwidth, low-latency networking, which makes synchronous replication practical.
> - A: Another Region protects against a Regional outage, but the much greater distance adds latency, so cross-Region copies are usually asynchronous.
> - B: Edge locations do not host databases.
> - C: Wavelength Zones serve ultra-low latency to 5G mobile devices; they are not for database standbys.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q59
In a standalone AWS account, the only IAM administrator accidentally removes her own permissions, and no other identity has IAM permissions. How can the permissions be restored?

- A. Sign in as the root user and edit the policies to restore the permissions
- B. Ask AWS Support to restore the permissions
- C. Use another IAM user's access keys to restore them
- D. Create a new AWS account and move the resources

> [!success]- Answer
> **A.** Restoring IAM user permissions when the only administrator has revoked their own is one of the tasks that requires root user credentials.
> - B: AWS Support does not change IAM permissions in customer accounts.
> - C: No other identity has IAM permissions, so no access keys could do this.
> - D: A new account is unnecessary; the root user can fix the account.
>
> Review: [[2.3 Access Management and IAM]]

### Q60
A consulting firm is considering joining the AWS Partner Network. Which TWO are benefits of becoming an AWS Partner? (Select TWO.)

- A. Free AWS usage for all of the firm's customers
- B. Enterprise Support at no charge
- C. AWS takes over responsibility for securing the firm's customers' workloads
- D. Access to partner training and certification
- E. Access to partner events

> [!success]- Answer
> **D and E.** Partner benefits include partner training and certification, partner events, and partner volume discounts.
> - A: Partnership does not make AWS usage free for anyone's customers.
> - B: Support plans are purchased separately; partnership does not include Enterprise Support.
> - C: The shared responsibility model does not change because a firm is an AWS Partner.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q61
Front-end developers want purpose-built tools to build and host a full-stack web and mobile application with user sign-in, data storage, and continuous deployment, without managing infrastructure. Which service should they use?

- A. AWS AppSync
- B. AWS Amplify
- C. AWS Device Farm
- D. AWS Elastic Beanstalk

> [!success]- Answer
> **B.** Amplify is a set of purpose-built tools and features for front-end web and mobile developers to build, deploy, and host full-stack applications.
> - A: AppSync creates GraphQL and pub/sub APIs; it is one piece a full-stack app might use, not the full toolset and hosting.
> - C: Device Farm tests apps on real mobile devices and browsers.
> - D: Elastic Beanstalk deploys and manages server-side web applications; it does not provide front-end and mobile tooling.
>
> Review: [[3.8 Other In-Scope Service Categories]]

### Q62
A company expands into Germany, Japan, and Brazil. Customers in each country need low latency, and some local laws require data to stay in that country. The company deploys its application in an AWS Region in each country within weeks, without building any data centers. Which benefit of the AWS Cloud does this demonstrate?

- A. Elasticity
- B. Economies of scale
- C. Global reach through AWS's global infrastructure
- D. High availability

> [!success]- Answer
> **C.** AWS's global infrastructure lets a company deploy in Regions around the world quickly, placing applications and data near users and inside the countries where they must stay.
> - A: Elasticity is scaling capacity with demand.
> - B: Economies of scale explain AWS's lower prices.
> - D: High availability is staying accessible through failures.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q63
Which resource can AWS WAF protect directly?

- A. A Network Load Balancer
- B. An Amazon EBS volume
- C. An Amazon RDS database
- D. An Amazon API Gateway REST API

> [!success]- Answer
> **D.** AWS WAF filters HTTP(S) requests for resources including Amazon CloudFront distributions, Application Load Balancers, and API Gateway REST APIs.
> - A: WAF does not attach to Network Load Balancers, which work at the transport layer rather than HTTP.
> - B: EBS volumes are storage and receive no web requests.
> - C: RDS databases are protected with security groups and network design, not WAF.
>
> Review: [[2.4 Security Components and Resources]]

### Q64
A data team needs a serverless service that discovers data in Amazon S3 and in databases, records its schema in a central data catalog, and runs extract, transform, and load (ETL) jobs to prepare the data for analytics. Which service should it use?

- A. AWS Glue
- B. Amazon QuickSight
- C. Amazon Kinesis
- D. Amazon OpenSearch Service

> [!success]- Answer
> **A.** Glue is a serverless data integration service that discovers data, catalogs it in the Glue Data Catalog, and runs ETL jobs.
> - B: QuickSight builds business intelligence dashboards; it does not catalog or transform data.
> - C: Kinesis collects and processes streaming data in near real time.
> - D: OpenSearch Service runs search and log analytics clusters.
>
> Review: [[3.7 AI-ML and Analytics Services]]

### Q65
A company wants to reduce operational overhead by moving to AWS managed services, in which AWS operates the underlying infrastructure and management software. Which TWO of the following are AWS managed services? (Select TWO.)

- A. A MySQL database the company installs on an EC2 instance
- B. Amazon RDS
- C. Amazon Elastic Container Service (Amazon ECS)
- D. Kubernetes that the company installs and operates on EC2 instances
- E. File server software the company runs on an EC2 instance

> [!success]- Answer
> **B and C.** Amazon RDS manages database setup, patching, and backups, and Amazon ECS is a fully managed container orchestration service.
> - A: A self-installed database on EC2 leaves patching, backups, and scaling to the company.
> - D: Self-installed Kubernetes leaves the control plane and nodes to the company.
> - E: Self-run file server software on EC2 is managed by the company.
>
> Review: [[1.4 Cloud Economics]]

---

## Scoring table

Mark each question 1 (correct) or 0 (wrong). Select TWO questions score 1 only if both choices are right.

| Q | Domain | Task statement | Answer | Score |
|---|---|---|---|---|
| 1 | 3 | 3.3 Compute | D | |
| 2 | 2 | 2.2 Security, governance, compliance | B | |
| 3 | 1 | 1.1 Benefits | A | |
| 4 | 3 | 3.8 Other in-scope services | C | |
| 5 | 2 | 2.1 Shared responsibility | A | |
| 6 | 4 | 4.2 Billing and cost management | D | |
| 7 | 1 | 1.2 Well-Architected | B | |
| 8 | 3 | 3.4 Database | C | |
| 9 | 2 | 2.4 Security components | A | |
| 10 | 3 | 3.2 Global infrastructure | D | |
| 11 | 1 | 1.4 Cloud economics | B | |
| 12 | 2 | 2.3 Access management | C | |
| 13 | 4 | 4.1 Pricing models | A | |
| 14 | 3 | 3.5 Network | D | |
| 15 | 2 | 2.2 Security, governance, compliance | B | |
| 16 | 1 | 1.3 Migration and CAF | C | |
| 17 | 3 | 3.6 Storage | A | |
| 18 | 2 | 2.3 Access management | D | |
| 19 | 3 | 3.1 Deploying and operating | C | |
| 20 | 1 | 1.2 Well-Architected | B, D | |
| 21 | 4 | 4.3 Support and resources | B | |
| 22 | 2 | 2.1 Shared responsibility | A, C | |
| 23 | 3 | 3.7 AI/ML and analytics | D | |
| 24 | 1 | 1.4 Cloud economics | A | |
| 25 | 2 | 2.4 Security components | C | |
| 26 | 3 | 3.2 Global infrastructure | A, E | |
| 27 | 1 | 1.3 Migration and CAF | B | |
| 28 | 4 | 4.1 Pricing models | D | |
| 29 | 3 | 3.3 Compute | A | |
| 30 | 2 | 2.1 Shared responsibility | C | |
| 31 | 3 | 3.5 Network | B | |
| 32 | 1 | 1.1 Benefits | D | |
| 33 | 2 | 2.2 Security, governance, compliance | A | |
| 34 | 3 | 3.8 Other in-scope services | B, C | |
| 35 | 4 | 4.2 Billing and cost management | C | |
| 36 | 2 | 2.3 Access management | B | |
| 37 | 1 | 1.2 Well-Architected | D | |
| 38 | 3 | 3.6 Storage | C | |
| 39 | 2 | 2.2 Security, governance, compliance | C, E | |
| 40 | 3 | 3.1 Deploying and operating | A | |
| 41 | 1 | 1.4 Cloud economics | B | |
| 42 | 2 | 2.4 Security components | D | |
| 43 | 4 | 4.3 Support and resources | C | |
| 44 | 3 | 3.5 Network | A, D | |
| 45 | 1 | 1.1 Benefits | A | |
| 46 | 2 | 2.1 Shared responsibility | B | |
| 47 | 3 | 3.6 Storage | D | |
| 48 | 2 | 2.3 Access management | C | |
| 49 | 1 | 1.3 Migration and CAF | B, E | |
| 50 | 3 | 3.7 AI/ML and analytics | C, D | |
| 51 | 4 | 4.1 Pricing models | A, B | |
| 52 | 2 | 2.2 Security, governance, compliance | A | |
| 53 | 3 | 3.4 Database | B | |
| 54 | 1 | 1.3 Migration and CAF | D | |
| 55 | 2 | 2.1 Shared responsibility | A | |
| 56 | 3 | 3.3 Compute | C | |
| 57 | 1 | 1.2 Well-Architected | B | |
| 58 | 3 | 3.2 Global infrastructure | D | |
| 59 | 2 | 2.3 Access management | A | |
| 60 | 4 | 4.3 Support and resources | D, E | |
| 61 | 3 | 3.8 Other in-scope services | B | |
| 62 | 1 | 1.1 Benefits | C | |
| 63 | 2 | 2.4 Security components | D | |
| 64 | 3 | 3.7 AI/ML and analytics | A | |
| 65 | 1 | 1.4 Cloud economics | B, C | |

### Totals by domain

| Domain | Questions | Your score | Percent | Target (90%) |
|---|---|---|---|---|
| 1 Cloud Concepts | 3, 7, 11, 16, 20, 24, 27, 32, 37, 41, 45, 49, 54, 57, 62, 65 | /16 | | 15 |
| 2 Security and Compliance | 2, 5, 9, 12, 15, 18, 22, 25, 30, 33, 36, 39, 42, 46, 48, 52, 55, 59, 63 | /19 | | 17 |
| 3 Cloud Technology and Services | 1, 4, 8, 10, 14, 17, 19, 23, 26, 29, 31, 34, 38, 40, 44, 47, 50, 53, 56, 58, 61, 64 | /22 | | 20 |
| 4 Billing, Pricing, and Support | 6, 13, 21, 28, 35, 43, 51, 60 | /8 | | 7 |
| **Total** | 65 | /65 | | 59 |

Questions per task statement: 1.1 ×4, 1.2 ×4, 1.3 ×4, 1.4 ×4; 2.1 ×5, 2.2 ×5, 2.3 ×5, 2.4 ×4; 3.1 ×2, 3.2 ×3, 3.3 ×3, 3.4 ×2, 3.5 ×3, 3.6 ×3, 3.7 ×3, 3.8 ×3; 4.1 ×3, 4.2 ×2, 4.3 ×3.

Any domain below 80%: reread that domain's task notes, then drill the matching flashcard deck and practice set ([[Practice - Domain 1]], [[Practice - Domain 2]], [[Practice - Domain 3 (Part 1)]], [[Practice - Domain 3 (Part 2)]], [[Practice - Domain 4]]). For look-alike misses, use [[Commonly Confused Services]]. Compare your result with [[Mock Exam 1]] and [[Mock Exam 2]]: a domain weak on all three exams needs your last review time. If you score 59 or more here, you are ready; spend the rest of the day on light review of [[Support Plans]], [[S3 Storage Classes]], and [[Shared Responsibility Model]] rather than new material.
