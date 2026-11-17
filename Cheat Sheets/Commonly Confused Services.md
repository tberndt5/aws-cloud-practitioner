---
tags:
  - clf-c02
  - cheat-sheet
aliases:
  - Look-alike services
---
# Commonly Confused Services

Each table lists look-alike services, what each does, and the **one cue** in a question stem that picks it. Learn the cue column. Most wrong answers on the CLF-C02 come from choosing a real service that sits next to the right one.

Related: [[Security Services at a Glance]] · [[Cost Management Tools]] · [[Compute Picker]] · [[Database Picker]] · [[Storage Picker]] · [[Networking and Gateways]] · [[Support Plans]] · [[Flashcards - Commonly Confused]]

---

## Security and governance

### Monitoring vs auditing vs configuration — [[2.2 Security, Governance, and Compliance Concepts]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Management and Governance#AWS CloudTrail\|AWS CloudTrail]] | Records API calls: who did what, when, from where | "**who** deleted / changed", "API activity", audit trail of actions |
| [[Services - Management and Governance#Amazon CloudWatch\|Amazon CloudWatch]] | Metrics, logs, alarms, dashboards for resources and apps | "**performance**", CPU utilization, alarm, log collection |
| [[Services - Management and Governance#AWS Config\|AWS Config]] | Inventory and history of resource configurations; rules evaluate compliance | "what did the resource **look like** on date X", "configuration drift", "is the bucket compliant" |

Mnemonic: CloudTrail = **T**rail of footprints (who). CloudWatch = **W**atch the gauges (how it performs). Config = **C**onfiguration snapshots (what it is).

### Threat and vulnerability services — [[2.2 Security, Governance, and Compliance Concepts]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Security, Identity, and Compliance#Amazon GuardDuty\|Amazon GuardDuty]] | ML threat detection from CloudTrail events, VPC Flow Logs, DNS logs | "malicious activity", "compromised instance", "crypto-mining", "unusual API calls" |
| [[Services - Security, Identity, and Compliance#Amazon Inspector\|Amazon Inspector]] | Scans EC2, container images in ECR, and Lambda for software vulnerabilities (CVEs) and unintended network exposure | "**vulnerabilities**", "CVE", "unpatched software" |
| [[Services - Security, Identity, and Compliance#Amazon Macie\|Amazon Macie]] | Finds sensitive data (PII) in **S3** | "PII", "credit card numbers in S3", "sensitive data discovery" |
| [[Services - Security, Identity, and Compliance#Amazon Detective\|Amazon Detective]] | Investigates findings to find root cause using graph analysis | "**investigate**", "root cause", "visualize what happened" |
| [[Services - Security, Identity, and Compliance#AWS Security Hub\|AWS Security Hub]] | Aggregates findings across services and accounts; runs best-practice checks | "**single view**", "aggregate / prioritize findings", "across accounts" |

Order of use: Inspector and Macie **find weaknesses**, GuardDuty **detects attacks**, Detective **investigates**, Security Hub **collects it all in one place**.

### Network protection — [[2.4 Security Components and Resources]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Security, Identity, and Compliance#AWS Shield\|AWS Shield]] | DDoS protection. Standard: free, automatic. Advanced: paid, 24/7 Shield Response Team, cost protection | "**DDoS**" |
| [[Services - Security, Identity, and Compliance#AWS WAF\|AWS WAF]] | Layer 7 web ACLs on CloudFront, ALB, API Gateway, AppSync | "SQL injection", "cross-site scripting", "block by IP/country/rate", HTTP(S) requests |
| [[Services - Security, Identity, and Compliance#AWS Firewall Manager\|AWS Firewall Manager]] | Centrally manages WAF, Shield Advanced, security groups, Network Firewall rules across accounts in an organization | "**across multiple accounts**", "centrally enforce firewall rules" |
| [[Services - Security, Identity, and Compliance#AWS Network Firewall\|AWS Network Firewall]] | Managed stateful firewall with intrusion detection and prevention for a **VPC** | "IDS/IPS", "filter traffic in and out of a VPC" |

### Security groups vs network ACLs — [[2.4 Security Components and Resources]], [[3.5 Network Services]]
| Feature | Security group | Network ACL |
|---|---|---|
| Level | Instance (elastic network interface) | **Subnet** |
| State | **Stateful**: return traffic allowed automatically | **Stateless**: return traffic needs its own rule |
| Rules | **Allow only** | Allow **and deny** |
| Evaluation | All rules evaluated together | Rules evaluated in number order, first match wins |
| Default | Denies all inbound, allows all outbound | Default NACL allows all in and out |

Cue: "**deny** a specific IP range" or "subnet level" means network ACL.

### Keys, certificates, and secrets — [[2.2 Security, Governance, and Compliance Concepts]], [[2.3 Access Management and IAM]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Security, Identity, and Compliance#AWS Key Management Service (AWS KMS)\|AWS KMS]] | Managed encryption keys on AWS-managed, multi-tenant HSMs; integrated with most services | "encryption keys", "encrypt EBS/S3/RDS at rest", default choice |
| [[Services - Security, Identity, and Compliance#AWS CloudHSM\|AWS CloudHSM]] | **Dedicated single-tenant** hardware security module; customer alone controls keys | "dedicated HSM", "sole control of keys", strict regulatory key custody |
| [[Services - Security, Identity, and Compliance#AWS Certificate Manager (ACM)\|AWS Certificate Manager (ACM)]] | Provisions, stores, and **renews SSL/TLS certificates** | "HTTPS", "SSL/TLS certificate", encryption **in transit** |
| [[Services - Security, Identity, and Compliance#AWS Secrets Manager\|AWS Secrets Manager]] | Stores credentials and **rotates them automatically** (built-in RDS rotation) | "**rotate** database passwords", "remove hard-coded credentials" |
| [[Services - Management and Governance#AWS Systems Manager\|Systems Manager Parameter Store]] | Stores configuration values and secrets as parameters; standard tier at no extra charge; no built-in rotation | "configuration data", "store parameters cheaply" |

### Identity — [[2.3 Access Management and IAM]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Security, Identity, and Compliance#AWS Identity and Access Management (IAM)\|AWS IAM]] | Users, groups, roles, policies controlling access **within an account** | "permissions", "policy", "role for an EC2 instance", "least privilege" |
| [[Services - Security, Identity, and Compliance#AWS IAM Identity Center (AWS Single Sign-On)\|AWS IAM Identity Center (AWS Single Sign-On)]] | Single sign-on for the **workforce** to multiple AWS accounts and business apps | "employees", "sign in once", "many accounts in AWS Organizations" |
| [[Services - Security, Identity, and Compliance#Amazon Cognito\|Amazon Cognito]] | Sign-up and sign-in for **customers of your web/mobile app**; social login | "app users", "millions of customers", "sign in with Google/Facebook" |
| [[Services - Security, Identity, and Compliance#AWS Directory Service\|AWS Directory Service]] | Managed **Microsoft Active Directory** in AWS | "Active Directory", "domain join", "Microsoft AD" |

### Compliance evidence — [[2.2 Security, Governance, and Compliance Concepts]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Security, Identity, and Compliance#AWS Artifact\|AWS Artifact]] | Self-service download of **AWS's** compliance reports (SOC, PCI, ISO) and agreements (BAA) | "AWS's SOC 2 report", "download compliance documents", "auditor wants proof AWS is compliant" |
| [[Services - Security, Identity, and Compliance#AWS Audit Manager\|AWS Audit Manager]] | Continuously collects evidence about **your** AWS usage mapped to frameworks | "collect **evidence** for **our** audit", "prepare for audit", "assessment reports" |
| [[Services - Management and Governance#AWS Config\|AWS Config]] | Evaluates resource configurations against rules | "rules", "configuration compliance", "remediate non-compliant resource" |

---

## Management, cost, and accounts

### Recommendations — [[2.4 Security Components and Resources]], [[4.3 Technical Resources and Support Options]], [[1.4 Cloud Economics]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Management and Governance#AWS Trusted Advisor\|AWS Trusted Advisor]] | Account-wide **best-practice checks**: cost optimization, performance, security, fault tolerance, service limits (quotas), operational excellence | "open ports", "root MFA", "idle resources", "service quotas", "best-practice checks" |
| [[Services - Management and Governance#AWS Compute Optimizer\|AWS Compute Optimizer]] | ML **rightsizing** recommendations for EC2, Auto Scaling groups, EBS, Lambda from utilization metrics | "**rightsize**", "over-provisioned instances", "optimal instance type" |
| [[Services - Management and Governance#AWS Well-Architected Tool\|AWS Well-Architected Tool]] | Questionnaire review of a **workload** against the six pillars | "review a **workload** against the pillars / framework" |
| [[Services - Cost Management#AWS Cost Explorer\|AWS Cost Explorer]] | Visualize and analyze **spend**; past 12 months plus 12-month forecast; RI and Savings Plans recommendations | "graph costs", "trends", "which service costs most" |

### Billing tools — [[4.2 Billing, Budget, and Cost Management]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Cost Management#AWS Budgets\|AWS Budgets]] | Set custom cost/usage/RI/Savings Plans budgets with **alerts** (actual or forecasted) | "**alert** when spend **will exceed**", "threshold", "notify" |
| [[Services - Cost Management#AWS Cost Explorer\|AWS Cost Explorer]] | Interactive charts of **past and forecast** spend | "visualize", "analyze", "trends" |
| [[Services - Cost Management#AWS Cost and Usage Report\|AWS Cost and Usage Report (CUR)]] | **Most detailed** line-item (up to hourly) data delivered to **S3**; query with Athena or QuickSight | "most **granular / comprehensive**", "line items", "hourly", "with cost allocation tags" |
| [[Services - Cost Management#AWS Pricing Calculator\|AWS Pricing Calculator]] | **Estimate** cost of a planned architecture before you build | "**estimate** before deploying", "new workload", "quote" |
| [[Services - Cost Management#AWS Billing Conductor\|AWS Billing Conductor]] | Custom pricing and pro forma bills for **showback/chargeback** | "reseller / partner", "custom rates", "chargeback to business units" |

Mnemonic: **Budgets = Before it hurts (alerts). Explorer = Eyeball the graph. CUR = Complete Unabridged Record. Calculator = Cost of the future. Conductor = Custom chargeback.**

### Multi-account — [[4.2 Billing, Budget, and Cost Management]], [[2.2 Security, Governance, and Compliance Concepts]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Management and Governance#AWS Organizations\|AWS Organizations]] | Group accounts into OUs, **consolidated billing**, service control policies (SCPs) | "consolidated billing", "SCP", "restrict what member accounts can do" |
| [[Services - Management and Governance#AWS Control Tower\|AWS Control Tower]] | Automated **landing zone** on top of Organizations with preconfigured guardrails (controls) | "**set up** a well-architected multi-account environment quickly", "landing zone", "guardrails" |
| [[Services - Management and Governance#AWS Service Catalog\|AWS Service Catalog]] | Catalog of **approved** products (CloudFormation templates) users can self-provision | "approved list of products", "self-service within standards" |

### AWS events vs your configuration — [[4.3 Technical Resources and Support Options]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Management and Governance#AWS Health Dashboard\|AWS Health Dashboard]] (+ AWS Health API) | **AWS-side** events affecting your resources: outages, scheduled maintenance, retirement notices | "AWS is doing maintenance on **my** instance", "service event in my Region" |
| [[Services - Management and Governance#AWS Trusted Advisor\|AWS Trusted Advisor]] | Checks **your** configuration against best practices | "my configuration", "recommendations" |

---

## Pricing models — [[4.1 AWS Pricing Models]]

### Dedicated Hosts vs Dedicated Instances
| Option | What it is | Cue |
|---|---|---|
| Dedicated Hosts | A whole **physical server** for you, with visibility of sockets and cores | "**BYOL** per-socket / per-core licenses", "server-bound licenses", "control instance placement on the host" |
| Dedicated Instances | Your instances run on hardware not shared with other accounts, but you do not see or control the host | "single-tenant hardware" with no licensing or host-visibility need |

### Reserved Instances vs Savings Plans
| Option | Commitment | Flexibility | Cue |
|---|---|---|---|
| Standard RI | Specific instance attributes, 1 or 3 years | Can change AZ, size within family (Linux); can sell on RI Marketplace | "steady state", "biggest RI discount" |
| Convertible RI | 1 or 3 years | Can exchange for different family, OS, tenancy | "may need to change instance family" |
| Compute Savings Plans | **$/hour spend**, 1 or 3 years | Any family, size, Region, OS; also **Fargate and Lambda** | "flexibility across Regions or services" |
| EC2 Instance Savings Plans | $/hour for one instance family in one Region | Size, OS, tenancy within that family | "committed to one family in one Region" |

RIs and Savings Plans both reach **up to 72%** off On-Demand. Spot reaches up to 90% but can be interrupted. RI and Savings Plans discounts are **shared across accounts** in an Organizations consolidated billing family by default. See [[EC2 Purchasing Options]].

---

## Application integration — [[3.8 Other In-Scope Service Categories]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Application Integration#Amazon Simple Notification Service (Amazon SNS)\|Amazon SNS]] | **Pub/sub push** to many subscribers (email, SMS, Lambda, SQS) | "notify", "fan-out", "alert by email/SMS" |
| [[Services - Application Integration#Amazon Simple Queue Service (Amazon SQS)\|Amazon SQS]] | **Queue**; consumers **pull** messages; buffers work | "**decouple**", "buffer", "queue", "consumer is slow / offline" |
| [[Services - Application Integration#Amazon EventBridge\|Amazon EventBridge]] | Event bus; rules route events from AWS services, SaaS apps, schedules | "react to **events** from AWS services or SaaS", "schedule", "event-driven" |
| [[Services - Application Integration#AWS Step Functions\|AWS Step Functions]] | Visual **workflow / state machine** coordinating steps | "orchestrate", "sequence of steps", "retries and branching" |

---

## Networking — [[3.5 Network Services]], [[3.1 Deploying and Operating in the AWS Cloud]]

### Edge and DNS
| Service | What it does | Cue |
|---|---|---|
| [[Services - Networking and Content Delivery#Amazon CloudFront\|Amazon CloudFront]] | CDN: **caches** content at edge locations | "cache", "static and dynamic web content", "reduce latency for downloads/video" |
| [[Services - Networking and Content Delivery#AWS Global Accelerator\|AWS Global Accelerator]] | Two **static anycast IPs**; routes TCP/UDP over the AWS backbone to the best healthy endpoint; **no caching** | "static IP", "UDP / gaming / VoIP", "non-HTTP", "fast regional failover" |
| [[Services - Networking and Content Delivery#Amazon Route 53\|Amazon Route 53]] | **DNS**: domain registration, routing policies, health checks | "domain name", "DNS", "latency/geolocation/failover routing" |

### Connectivity
| Service | What it does | Cue |
|---|---|---|
| [[Services - Networking and Content Delivery#AWS Direct Connect\|AWS Direct Connect]] | **Dedicated private physical** link from your data center to AWS; not over the internet; not encrypted by default; takes weeks to set up | "consistent performance", "does not traverse the internet", "high bandwidth" |
| [[Services - Networking and Content Delivery#AWS VPN\|AWS Site-to-Site VPN]] | **Encrypted IPsec** tunnel from an on-premises network to a VPC over the internet | "quick to set up", "encrypted over the internet", backup for Direct Connect |
| [[Services - Networking and Content Delivery#AWS VPN\|AWS Client VPN]] | Managed VPN for **individual users'** devices | "remote employees' laptops" |

### Connect vs Direct Connect
| Service | What it is | Cue |
|---|---|---|
| [[Services - Business Productivity#Amazon Connect\|Amazon Connect]] | Omnichannel cloud **contact center** | "call center", "customer service agents", "IVR" |
| [[Services - Networking and Content Delivery#AWS Direct Connect\|AWS Direct Connect]] | **Network** connection | "private link to AWS" |

### Edge infrastructure — [[3.2 AWS Global Infrastructure]]
| Option | What it is | Cue |
|---|---|---|
| Edge locations | Sites for CloudFront, Route 53, Global Accelerator, Shield | "cache content near users", "more edge locations than Regions" |
| [[Services - Compute#AWS Local Zones\|AWS Local Zones]] | AWS compute/storage in a **metro area** near large population or industry centers | "single-digit ms latency for users in **a city**", media rendering, real-time gaming in a metro |
| [[Services - Compute#AWS Wavelength\|AWS Wavelength]] | AWS infrastructure inside **5G carrier networks** | "**5G**", "mobile devices", "telecom provider" |
| [[Services - Compute#AWS Outposts\|AWS Outposts]] | AWS-managed racks in **your own data center** | "on premises", "data must stay in our facility", "local data processing in our building" |

---

## Compute and deployment — [[3.3 Compute Services]], [[3.1 Deploying and Operating in the AWS Cloud]]

### Containers and serverless
| Service | What it does | Cue |
|---|---|---|
| [[Services - Containers#Amazon Elastic Container Service (Amazon ECS)\|Amazon ECS]] | AWS-native container **orchestration** | "Docker containers", AWS-native orchestration |
| [[Services - Containers#Amazon Elastic Kubernetes Service (Amazon EKS)\|Amazon EKS]] | Managed **Kubernetes** control plane | "**Kubernetes**", "portable", "already use K8s on premises" |
| [[Services - Serverless#AWS Fargate\|AWS Fargate]] | **Serverless compute engine** for ECS and EKS containers | "containers **without managing servers / EC2 instances**" |
| [[Services - Containers#Amazon Elastic Container Registry (Amazon ECR)\|Amazon ECR]] | Container **image registry** | "store / version container images" |
| [[Services - Serverless#AWS Lambda\|AWS Lambda]] | Event-driven **functions**, max 15 minutes per invocation, billed per request and ms | "run **code** in response to events", "no servers", short tasks |

### Deployment platforms
| Service | What it does | Cue |
|---|---|---|
| [[Services - Compute#AWS Elastic Beanstalk\|AWS Elastic Beanstalk]] | Upload **application code**; AWS provisions and manages capacity, load balancing, scaling (PaaS) | "developers just upload code", "no infrastructure knowledge" |
| [[Services - Management and Governance#AWS CloudFormation\|AWS CloudFormation]] | **Infrastructure as code** templates (JSON/YAML) | "**template**", "repeatable", "same environment in many Regions/accounts" |
| [[Services - Compute#Amazon Lightsail\|Amazon Lightsail]] | Simple **bundled** VPS: instance, storage, data transfer at a **fixed monthly price** | "simple", "small website/WordPress", "predictable low monthly price", little AWS experience |

### Developer tools — [[3.8 Other In-Scope Service Categories]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Developer Tools#AWS CodeCommit\|AWS CodeCommit]] | Private **Git repositories** | "source control", "Git" |
| [[Services - Developer Tools#AWS CodeBuild\|AWS CodeBuild]] | **Compiles** code, runs tests, produces artifacts | "build", "compile", "unit tests" |
| [[Services - Developer Tools#AWS CodeDeploy\|AWS CodeDeploy]] | Automates **deployments** to EC2, on-premises servers, Lambda, ECS | "deploy to servers", "rolling / blue-green deployment" |
| [[Services - Developer Tools#AWS CodePipeline\|AWS CodePipeline]] | Orchestrates the whole **CI/CD release pipeline** | "automate release process end to end", "continuous delivery" |
| [[Services - Developer Tools#AWS CodeArtifact\|AWS CodeArtifact]] | **Package** repository (npm, Maven, PyPI) | "software packages", "dependencies" |
| [[Services - Developer Tools#AWS CodeStar\|AWS CodeStar]] | Unified project dashboard that sets up the whole toolchain | "quickly start a project with a full toolchain" |

Order: Commit (store) → Build (compile/test) → Deploy (release), with Pipeline wrapping all three.
Current status: AWS CodeStar reached end of support on July 25, 2024 (AWS General Reference, Services in Full Shutdown).

### Shells and IDEs
| Tool | What it is | Cue |
|---|---|---|
| [[Services - Developer Tools#AWS Cloud9\|AWS Cloud9]] | Browser-based **IDE** (editor, debugger, terminal) | "write, run, debug code in a browser", "IDE" |
| [[Services - Developer Tools#AWS CloudShell\|AWS CloudShell]] | Browser-based **shell**, pre-authenticated with your console credentials, CLI preinstalled | "run CLI commands from the console without installing anything" |
| [[Services - Developer Tools#AWS CLI\|AWS CLI]] | Command-line tool you install locally | "scripts", "automate from my terminal" |

Current status: AWS Cloud9 has been closed to new customers since July 25, 2024; existing customers can keep using it.

---

## Storage — [[3.6 Storage Services]]
| Service | Type | Cue |
|---|---|---|
| [[Services - Storage#Amazon Elastic Block Store (Amazon EBS)\|Amazon EBS]] | **Block**, persistent, attached to one EC2 instance in **one AZ** (Multi-Attach is a narrow exception) | "boot volume", "database disk on EC2", "persists after stop" |
| Instance store | **Block**, physically attached to the host, **ephemeral** | "temporary data, cache, buffer", "lost when instance stops" |
| [[Services - Storage#Amazon Elastic File System (Amazon EFS)\|Amazon EFS]] | **File** (NFS), Linux, shared by many instances across AZs, scales automatically | "shared file system for **Linux**", "many instances at once" |
| [[Services - Storage#Amazon FSx\|Amazon FSx]] | **File**: Windows File Server (SMB, AD), Lustre (HPC), NetApp ONTAP, OpenZFS | "**Windows** file shares", "SMB", "Lustre / HPC" |
| [[Services - Storage#Amazon S3\|Amazon S3]] | **Object**, virtually unlimited, 11 nines durability | "objects", "static website", "data lake", "backups", "any amount of data" |
| [[Services - Storage#AWS Storage Gateway\|AWS Storage Gateway]] | **Hybrid**: on-premises appliance giving local apps cached access to cloud storage | "on-premises apps need access to cloud storage", "cached", "tape backup to cloud" |

## Databases — [[3.4 Database Services]]
| Service | Type | Cue |
|---|---|---|
| [[Services - Database#Amazon RDS\|Amazon RDS]] | Managed **relational** (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Db2) | "relational", "SQL", "existing Oracle/SQL Server", "managed" |
| [[Services - Database#Amazon Aurora\|Amazon Aurora]] | AWS-built **relational**, MySQL/PostgreSQL compatible, higher performance, 6 copies across 3 AZs | "MySQL/PostgreSQL compatible with **higher performance** / availability" |
| [[Services - Database#Amazon DynamoDB\|Amazon DynamoDB]] | Serverless **NoSQL key-value/document**, single-digit ms at any scale | "key-value", "schemaless", "millions of requests per second" |
| [[Services - Analytics#Amazon Redshift\|Amazon Redshift]] | **Data warehouse** (OLAP), columnar, petabyte scale | "analytics / BI on historical data", "data warehouse", "complex queries" |
| [[Services - Database#Amazon ElastiCache\|Amazon ElastiCache]] | In-memory **cache** (Redis, Memcached) in front of a database | "**cache**", "reduce load on the database", "session store" |
| [[Services - Database#Amazon MemoryDB for Redis\|Amazon MemoryDB for Redis]] | **Durable** in-memory **primary database**, Redis compatible | "in-memory **and durable**", "primary database with microsecond reads" |
| [[Services - Database#Amazon Neptune\|Amazon Neptune]] | **Graph** database | "relationships", "social network", "fraud rings", "recommendation graph" |

## Analytics — [[3.7 AI-ML and Analytics Services]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Analytics#Amazon Athena\|Amazon Athena]] | Serverless **SQL queries directly on S3** | "query data **in S3** with SQL", "ad hoc", "no loading" |
| [[Services - Analytics#Amazon Redshift\|Amazon Redshift]] | Data warehouse you load data into | "data warehouse", "complex BI queries at scale" |
| [[Services - Analytics#Amazon EMR\|Amazon EMR]] | Managed **Hadoop / Spark** clusters | "Hadoop", "Spark", "big data framework" |
| [[Services - Analytics#AWS Glue\|AWS Glue]] | Serverless **ETL** and Data Catalog | "ETL", "prepare / transform data", "crawler", "catalog" |
| [[Services - Analytics#Amazon Kinesis\|Amazon Kinesis]] | **Real-time streaming** ingestion and processing | "real time", "clickstream", "IoT telemetry", "video streams" |
| [[Services - Analytics#Amazon QuickSight\|Amazon QuickSight]] | **BI dashboards** and visualizations | "dashboards", "business intelligence", "visualize" |
| [[Services - Analytics#Amazon OpenSearch Service\|Amazon OpenSearch Service]] | Search and **log analytics** clusters | "full-text search", "log analytics", "Elasticsearch / OpenSearch" |

Current status: QuickSight is now AWS Quick Sight, part of AWS Quick (renamed November 2026; formerly Amazon Quick Suite). The exam uses "Amazon QuickSight".

## Migration and transfer (mention level) — [[1.3 Migration Strategies and AWS CAF]], [[3.4 Database Services]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - Migration and Transfer#AWS Database Migration Service (AWS DMS)\|AWS DMS]] | Migrates **data** between databases with minimal downtime (source stays live) | "migrate database", "continuous replication", "minimal downtime" |
| [[Services - Migration and Transfer#AWS Schema Conversion Tool (AWS SCT)\|AWS SCT]] | Converts **schema** and code between **different** engines | "**heterogeneous**", "Oracle to Aurora PostgreSQL", "convert stored procedures" |
| [[Services - Migration and Transfer#AWS Application Migration Service\|AWS Application Migration Service]] | Automated **lift-and-shift (rehost)** of servers | "rehost servers", "replicate VMs to EC2" |
| [[Services - Migration and Transfer#AWS Migration Hub\|AWS Migration Hub]] | Central place to **track** migration progress | "track status of migrations" |
| [[Services - Migration and Transfer#AWS Application Discovery Service\|AWS Application Discovery Service]] | Collects **on-premises server inventory** and usage to plan | "discover", "inventory", "dependencies before migrating" |
| [[Services - Migration and Transfer#AWS Snow Family\|AWS Snow Family]] | **Physical** devices for offline transfer and edge compute | "terabytes/petabytes", "limited bandwidth", "no connectivity" |
| [[Services - Migration and Transfer#AWS Transfer Family\|AWS Transfer Family]] | Managed **SFTP / FTPS / FTP** endpoints into S3 or EFS | "partners upload with **SFTP**" |
| AWS DataSync | **Online** agent-based transfer from NFS/SMB/HDFS to S3, EFS, FSx | "online transfer", "sync file shares over the network" |

Current status: AWS Migration Hub and AWS Snowball Edge closed to new customers on November 7, 2025; AWS Snowmobile reached end of support March 14, 2024.

## Machine learning — [[3.7 AI-ML and Analytics Services]]
| Service | Input → output | Cue |
|---|---|---|
| [[Services - Machine Learning#Amazon Comprehend\|Amazon Comprehend]] | Text → **meaning** (sentiment, entities, key phrases) | "sentiment", "NLP insights from text" |
| [[Services - Machine Learning#Amazon Kendra\|Amazon Kendra]] | Question → answer from your documents (**enterprise search**) | "search internal documents in natural language" |
| [[Services - Machine Learning#Amazon Lex\|Amazon Lex]] | Conversation → **chatbot** (voice and text) | "chatbot", "conversational interface" |
| [[Services - Machine Learning#Amazon Polly\|Amazon Polly]] | Text → **speech** | "read text aloud", "lifelike voice" |
| [[Services - Machine Learning#Amazon Transcribe\|Amazon Transcribe]] | Speech → **text** | "transcripts", "captions", "speech to text" |
| [[Services - Machine Learning#Amazon Translate\|Amazon Translate]] | Text → **other language** | "translate", "multilingual" |
| [[Services - Machine Learning#Amazon Textract\|Amazon Textract]] | Scanned document → **text, forms, tables** | "extract text from scanned forms / PDFs", "handwriting" |
| [[Services - Machine Learning#Amazon Rekognition\|Amazon Rekognition]] | Image/video → **labels, faces, objects** | "image", "video", "facial analysis", "content moderation" |
| [[Services - Machine Learning#Amazon SageMaker\|Amazon SageMaker]] | Build, train, deploy **your own** models | "data scientists build custom models" |

Memory: **Polly** speaks (parrot); **Transcribe** writes down what it hears; **Textract** reads paper; **Rekognition** sees.

## End-user computing, frontend, IoT — [[3.8 Other In-Scope Service Categories]]
| Service | What it does | Cue |
|---|---|---|
| [[Services - End-User Computing#Amazon WorkSpaces\|Amazon WorkSpaces]] | Full persistent **virtual desktop** (DaaS) | "virtual desktop", "remote employees need a full Windows/Linux desktop" |
| [[Services - End-User Computing#Amazon AppStream 2.0\|Amazon AppStream 2.0]] | **Streams individual desktop applications** to a browser | "stream an **application**", "no full desktop" |
| [[Services - End-User Computing#Amazon WorkSpaces Web\|Amazon WorkSpaces Web]] | Secure **browser** access to internal websites and SaaS apps | "internal web apps / SaaS through a secure browser" |
| [[Services - Frontend Web and Mobile#AWS Amplify\|AWS Amplify]] | Build, deploy, and **host full-stack** web and mobile apps | "frontend developers", "host web app", "full-stack quickly" |
| [[Services - Frontend Web and Mobile#AWS AppSync\|AWS AppSync]] | Managed **GraphQL** and pub/sub APIs | "**GraphQL**", "real-time data sync" |
| [[Services - Internet of Things (IoT)#AWS IoT Core\|AWS IoT Core]] | Connects devices to the **cloud**, routes messages (MQTT) | "connect billions of devices", "device messages to AWS" |
| [[Services - Internet of Things (IoT)#AWS IoT Greengrass\|AWS IoT Greengrass]] | Runs AWS logic **on the device at the edge**, works offline | "**local** processing on devices", "intermittent connectivity" |

Current status: Amazon WorkSpaces Web was renamed Amazon WorkSpaces Secure Browser on May 20, 2024, and the product page says it will no longer be open to new customers starting October 29, 2026.

## Help from people — [[4.3 Technical Resources and Support Options]], [[3.8 Other In-Scope Service Categories]]
| Option | What it is | Cue |
|---|---|---|
| AWS Professional Services | AWS's own **consulting** organization for large engagements | "AWS experts to help achieve a business outcome / migration program" |
| AWS Solutions Architects | AWS technical experts who give **architecture guidance** | "design guidance from AWS" |
| [[Services - Customer Engagement#AWS Managed Services (AMS)\|AWS Managed Services (AMS)]] | AWS **operates** your infrastructure day to day (patching, monitoring, backup) | "outsource ongoing operations", "lack staff to run it" |
| [[Services - Customer Engagement#AWS IQ\|AWS IQ]] | Marketplace to hire **AWS Certified freelancers** for on-demand projects | "hire a certified expert for a short project", pay through AWS |
| AWS Partner Network (APN) | Consulting partners / system integrators and ISVs (technology partners) | "third-party firm", "system integrator", "ISV" |
| [[Services - Customer Engagement#AWS Support\|AWS Support]] | Case-based help from Cloud Support Engineers; TAM on Enterprise plans | "open a support case", "TAM" |

Current status: AWS IQ reached end of support in May 2026 (AWS General Reference lists May 20, 2026).

---

## If the question says X, answer Y
- "Who made this change" → CloudTrail. "What did it look like before" → Config. "CPU high, alarm" → CloudWatch.
- "AWS's compliance report" → Artifact. "Evidence for our audit" → Audit Manager.
- "Vulnerability / CVE" → Inspector. "PII in S3" → Macie. "Threat / malicious" → GuardDuty. "Root cause" → Detective. "One pane for findings" → Security Hub.
- "DDoS" → Shield. "SQL injection / XSS" → WAF. "Across all accounts" → Firewall Manager. "VPC IDS/IPS" → Network Firewall.
- "Deny an IP" or "stateless" → network ACL. "Stateful, instance level" → security group.
- "Rotate secrets" → Secrets Manager. "Dedicated HSM" → CloudHSM. "TLS certificate" → ACM.
- "Employees, many accounts, single sign-on" → IAM Identity Center. "App customers sign in" → Cognito. "Active Directory" → Directory Service.
- "Alert before overspending" → Budgets. "Most detailed bill data" → CUR. "Estimate before building" → Pricing Calculator. "Chargeback with custom rates" → Billing Conductor.
- "Rightsize" → Compute Optimizer. "Best-practice checks incl. security and quotas" → Trusted Advisor.
- "Decouple / buffer" → SQS. "Fan-out notification" → SNS. "React to events / schedule" → EventBridge. "Orchestrate steps" → Step Functions.
- "Static IP, UDP" → Global Accelerator. "Cache" → CloudFront. "DNS" → Route 53.
- "5G" → Wavelength. "Metro area" → Local Zones. "Our data center" → Outposts.
- "Containers, no servers" → Fargate. "Kubernetes" → EKS. "Store images" → ECR.
- "Upload code, AWS handles the rest" → Elastic Beanstalk. "Template" → CloudFormation. "Simple fixed monthly price" → Lightsail.
- "Shared Linux file system" → EFS. "Windows SMB" → FSx for Windows File Server. "Temporary, lost on stop" → instance store.
- "Graph" → Neptune. "Data warehouse" → Redshift. "SQL on S3" → Athena. "Durable in-memory" → MemoryDB.
- "Server-bound licenses" → Dedicated Hosts. "Commit spend across EC2, Fargate, Lambda" → Compute Savings Plans.
