---
tags:
  - clf-c02
  - practice
  - domain-3
---
# Practice - Domain 3 (Part 1)

Twenty original questions on task statements 3.1 to 3.4. Answer each before opening the callout.

### Q1
A company's operations team must deploy the same network, compute, and database resources in three AWS Regions and wants every deployment to be identical and reviewable in version control. Which approach meets these requirements?

- A. Use the AWS Management Console to create the resources in each Region
- B. Define the resources in AWS CloudFormation templates and deploy them in each Region
- C. Use AWS CloudShell to run commands interactively in each Region
- D. Deploy the application with Amazon Lightsail in each Region

> [!success]- Answer
> **B.** CloudFormation is infrastructure as code: one template produces identical, repeatable stacks and can be stored in version control.
> - A: Manual console work is error-prone and not repeatable.
> - C: Interactive commands are one-time operations, not a versioned definition.
> - D: Lightsail offers simple bundled servers, not a way to define and replicate infrastructure.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q2
A developer is writing a Java application that must read and write objects in Amazon S3. What is the most appropriate way for the application to access S3?

- A. AWS Management Console
- B. AWS CLI
- C. AWS SDK for Java
- D. AWS CloudFormation

> [!success]- Answer
> **C.** The AWS SDKs let application code call AWS services in the developer's programming language.
> - A: The console is for people using a browser, not application code.
> - B: The CLI is for terminal commands and scripts.
> - D: CloudFormation provisions infrastructure; it does not perform application reads and writes.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q3
A company needs a connection between its data center and its VPC that provides consistent network performance and does not travel over the public internet. Which AWS service should it use?

- A. AWS Site-to-Site VPN
- B. AWS Client VPN
- C. AWS Direct Connect
- D. Amazon CloudFront

> [!success]- Answer
> **C.** Direct Connect is a private, dedicated network connection that bypasses the public internet and gives consistent performance.
> - A: Site-to-Site VPN is encrypted but runs over the public internet.
> - B: Client VPN connects individual users, also over the internet.
> - D: CloudFront is a content delivery network, not a private connection.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q4
A manufacturer must process data from factory equipment with very low latency inside its own facility, and it wants to use the same AWS APIs and tools it uses in the cloud. Which service meets this requirement?

- A. AWS Local Zones
- B. AWS Outposts
- C. AWS Wavelength
- D. Amazon EC2 Dedicated Hosts

> [!success]- Answer
> **B.** Outposts extends AWS infrastructure, services, APIs, and tools to the customer's premises, a hybrid deployment.
> - A: Local Zones are AWS-run sites in metro areas, not the customer's facility.
> - C: Wavelength runs inside telecom 5G networks.
> - D: Dedicated Hosts are physical servers in AWS data centers, not on premises.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q5
Which statements describe a hybrid cloud deployment? (Select TWO.)

- A. All application components run in the AWS Cloud
- B. Cloud-based resources are connected to infrastructure that remains on premises
- C. Resources run only in the company's data center using virtualization tools
- D. A company keeps a legacy system on premises while moving new workloads to AWS
- E. A company runs workloads in two AWS Regions

> [!success]- Answer
> **B and D.** Hybrid means connecting cloud resources with infrastructure that stays on premises, often during a gradual migration.
> - A: That is the cloud (all-in) model.
> - C: That is the on-premises (private cloud) model.
> - E: Multiple Regions is still a cloud deployment.
>
> Review: [[3.1 Deploying and Operating in the AWS Cloud]]

### Q6
Which statement correctly describes an AWS Availability Zone?

- A. A worldwide network of data centers that caches content close to users
- B. One or more discrete data centers within an AWS Region
- C. An isolated geographic area that contains multiple Regions
- D. A telecom-hosted site that runs AWS services in a 5G network

> [!success]- Answer
> **B.** An AZ is one or more data centers within a Region, with redundant power, networking, and connectivity.
> - A: That describes edge locations.
> - C: Regions contain AZs, not the other way around.
> - D: That describes Wavelength Zones.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q7
A company runs its web application on EC2 instances in a single Availability Zone. Leadership wants the application to keep running if a data center fails. What should the company do?

- A. Move to a larger EC2 instance type
- B. Deploy instances in multiple Availability Zones behind an Elastic Load Balancer
- C. Serve the application through Amazon CloudFront
- D. Purchase Reserved Instances for the existing instances

> [!success]- Answer
> **B.** AZs do not share single points of failure, so running across multiple AZs behind a load balancer keeps the application available if one fails.
> - A: A larger instance is still a single point of failure in one AZ.
> - C: CloudFront caches content but does not make the origin highly available.
> - D: Reserved Instances change pricing, not availability.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q8
A European bank must store customer data only within Germany. Which factor should drive its choice of AWS Region first?

- A. Lowest price per instance hour
- B. Number of available services
- C. Data sovereignty and compliance requirements
- D. Proximity to the company's developers

> [!success]- Answer
> **C.** Legal and regulatory requirements such as data sovereignty come first; they rule out Regions regardless of price or features.
> - A: Pricing matters only among Regions that already meet compliance needs.
> - B: Service availability is considered after compliance.
> - D: Latency is about end users, and it still ranks below legal requirements.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q9
A global online game uses UDP and needs fixed IP addresses that players connect to, with traffic carried over the AWS network to the nearest healthy Regional endpoint. Which service meets these needs?

- A. Amazon CloudFront
- B. AWS Global Accelerator
- C. Amazon Route 53
- D. AWS Direct Connect

> [!success]- Answer
> **B.** Global Accelerator provides static anycast IP addresses and routes TCP and UDP traffic over the AWS global network to healthy endpoints.
> - A: CloudFront caches HTTP(S) content and doesn't give static IPs for UDP games.
> - C: Route 53 is DNS; it doesn't carry traffic over the AWS backbone.
> - D: Direct Connect links a customer data center to AWS, not players.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q10
Which are valid reasons to deploy a workload in more than one AWS Region? (Select TWO.)

- A. Recover from a disaster that affects an entire Region
- B. Protect against the failure of a single data center
- C. Reduce latency for users on different continents
- D. Get access to edge locations
- E. Avoid the need for a load balancer

> [!success]- Answer
> **A and C.** Multiple Regions support disaster recovery and business continuity and serve global users with lower latency (and help with data sovereignty).
> - B: A single data center failure is handled by multiple AZs in one Region.
> - D: Edge locations are available to every Region's workloads through CloudFront and Global Accelerator.
> - E: Multi-Region designs still use load balancers.
>
> Review: [[3.2 AWS Global Infrastructure]]

### Q11
A media company transcodes thousands of video files every day. The work is CPU-intensive. Which EC2 instance family is the best fit?

- A. Memory optimized
- B. Storage optimized
- C. Compute optimized
- D. General purpose

> [!success]- Answer
> **C.** Compute optimized instances suit CPU-bound work such as media transcoding, batch processing, and game servers.
> - A: Memory optimized suits large in-memory data sets.
> - B: Storage optimized suits heavy local disk I/O.
> - D: General purpose balances resources and is not the best fit for CPU-bound work.
>
> Review: [[3.3 Compute Services]]

### Q12
A team already runs its containerized applications on Kubernetes on premises and wants a managed Kubernetes service on AWS without operating the control plane. Which service should it use?

- A. Amazon ECS
- B. Amazon EKS
- C. Amazon ECR
- D. AWS Elastic Beanstalk

> [!success]- Answer
> **B.** Amazon EKS runs Kubernetes without the need to install or operate the Kubernetes control plane.
> - A: ECS is AWS's own orchestrator, not Kubernetes.
> - C: ECR stores container images; it does not run them.
> - D: Elastic Beanstalk deploys web applications, not Kubernetes clusters.
>
> Review: [[3.3 Compute Services]]

### Q13
A company wants to run a long-running containerized service without provisioning, patching, or scaling any EC2 instances. Which option should it choose?

- A. AWS Lambda
- B. Amazon ECS on EC2 instances it manages
- C. AWS Fargate
- D. Amazon Lightsail

> [!success]- Answer
> **C.** Fargate is serverless compute for containers with ECS or EKS, with no servers to manage and no 15-minute limit.
> - A: Lambda runs functions up to 15 minutes, not long-running containers.
> - B: ECS on EC2 means the company manages the instances.
> - D: Lightsail provides simple virtual servers that the company still manages.
>
> Review: [[3.3 Compute Services]]

### Q14
Traffic to a retail website rises sharply in the evening and drops overnight. The company wants capacity to follow demand automatically so it pays only for what it needs. Which combination achieves this? (Select TWO.)

- A. Amazon EC2 Auto Scaling
- B. Elastic Load Balancing
- C. AWS Direct Connect
- D. Amazon EC2 Dedicated Hosts
- E. AWS Schema Conversion Tool

> [!success]- Answer
> **A and B.** Auto Scaling adds and removes instances to match demand (elasticity), and the load balancer spreads requests across whichever instances are running.
> - C: Direct Connect is a private network connection.
> - D: Dedicated Hosts are a purchasing and tenancy option and don't scale automatically.
> - E: SCT converts database schemas.
>
> Review: [[3.3 Compute Services]]

### Q15
A security team must send all incoming VPC traffic through a fleet of third-party virtual firewall appliances that can scale with demand. Which load balancer type is designed for this?

- A. Application Load Balancer
- B. Network Load Balancer
- C. Gateway Load Balancer
- D. Classic Load Balancer

> [!success]- Answer
> **C.** Gateway Load Balancer deploys, scales, and manages third-party virtual network appliances such as firewalls and intrusion prevention systems.
> - A: ALB routes HTTP/HTTPS requests at layer 7.
> - B: NLB handles high-performance TCP/UDP traffic at layer 4.
> - D: Classic Load Balancer is previous generation and not meant for appliances.
>
> Review: [[3.3 Compute Services]]

### Q16
A company runs MySQL on EC2 and spends many hours on patching, backups, and failover. It wants AWS to handle these tasks while keeping a relational MySQL-compatible database. Which service should it migrate to?

- A. Amazon DynamoDB
- B. Amazon RDS for MySQL
- C. Amazon Redshift
- D. Amazon Neptune

> [!success]- Answer
> **B.** Amazon RDS is a managed relational database: AWS handles patching, automated backups, and Multi-AZ failover.
> - A: DynamoDB is NoSQL, not MySQL-compatible.
> - C: Redshift is a data warehouse for analytics.
> - D: Neptune is a graph database.
>
> Review: [[3.4 Database Services]]

### Q17
An application on Amazon RDS is slowed by heavy reporting queries that only read data. Which feature best improves read performance?

- A. Multi-AZ deployment
- B. Read replicas
- C. Automated backups
- D. Manual snapshots

> [!success]- Answer
> **B.** Read replicas are asynchronous read-only copies that offload read traffic from the primary.
> - A: Multi-AZ provides high availability; the classic standby does not serve reads.
> - C: Automated backups enable point-in-time recovery, not performance.
> - D: Snapshots are backups.
>
> Review: [[3.4 Database Services]]

### Q18
A mobile game stores player profiles and session data as key-value items, must handle millions of requests per second with single-digit millisecond latency, and should require no server management. Which database fits best?

- A. Amazon Aurora
- B. Amazon DynamoDB
- C. Amazon ElastiCache
- D. Amazon RDS for PostgreSQL

> [!success]- Answer
> **B.** DynamoDB is a serverless key-value and document NoSQL database with single-digit millisecond performance at any scale.
> - A: Aurora is relational and not the natural fit for schemaless key-value data.
> - C: ElastiCache is a cache, not the durable primary store.
> - D: RDS for PostgreSQL is relational and requires instance sizing.
>
> Review: [[3.4 Database Services]]

### Q19
A company wants to reduce read latency from milliseconds to microseconds for frequently accessed data and lower the load on its relational database. Which service should it add?

- A. Amazon Neptune
- B. Amazon Redshift
- C. Amazon ElastiCache
- D. AWS Database Migration Service

> [!success]- Answer
> **C.** ElastiCache is an in-memory cache that serves frequently read data in microseconds and offloads the database.
> - A: Neptune is a graph database.
> - B: Redshift is a data warehouse for analytics.
> - D: DMS migrates databases; it doesn't cache.
>
> Review: [[3.4 Database Services]]

### Q20
A company is moving an on-premises Oracle database to Amazon Aurora PostgreSQL with minimal downtime. Which tools should it use? (Select TWO.)

- A. AWS Schema Conversion Tool to convert the schema and code
- B. AWS Database Migration Service to migrate the data while the source stays online
- C. AWS Application Migration Service to rehost the database server
- D. Amazon Redshift to stage the data
- E. AWS CloudFormation to convert the stored procedures

> [!success]- Answer
> **A and B.** This is a heterogeneous migration (different engines): SCT converts the schema first, then DMS migrates the data with the source still operational.
> - C: Application Migration Service rehosts servers as-is and would not change the engine.
> - D: Redshift is a data warehouse, not a migration tool.
> - E: CloudFormation provisions infrastructure; it doesn't convert database code.
>
> Review: [[3.4 Database Services]]
