---
tags:
  - clf-c02
  - practice
  - domain-1
---
# Practice - Domain 1: Cloud Concepts

20 original exam-style questions. Answer each before opening the callout. Notes: [[1.1 Benefits of the AWS Cloud]] · [[1.2 Design Principles - Well-Architected Framework]] · [[1.3 Migration Strategies and AWS CAF]] · [[1.4 Cloud Economics]]

### Q1
A retail startup expects traffic to its website to grow, but cannot predict by how much. The founders do not want to buy servers that may sit idle or run out of capacity during a promotion. Which advantage of cloud computing addresses this concern most directly?

- A. Benefit from massive economies of scale
- B. Stop guessing capacity
- C. Go global in minutes
- D. Stop spending money running and maintaining data centers

> [!success]- Answer
> **B.** "Stop guessing capacity" is the advantage that removes the risk of over- or under-provisioning when demand is unknown.
> - A: Economies of scale explain lower prices from AWS's size, not capacity planning.
> - C: Going global is about deploying in other Regions for latency.
> - D: This is about avoiding data center operations work, not sizing.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q2
Which statement best describes how AWS economies of scale benefit customers?

- A. Customers receive a discount when they commit to a 1-year or 3-year term.
- B. Customers can deploy resources in multiple Regions within minutes.
- C. Aggregated usage across many customers lets AWS achieve lower costs, which result in lower pay-as-you-go prices.
- D. Customers can automatically add and remove capacity based on demand.

> [!success]- Answer
> **C.** Economies of scale come from AWS's aggregated usage, which lowers its unit costs and the prices it charges.
> - A: Commitment discounts are a pricing model (Reserved Instances, Savings Plans), not economies of scale.
> - B: That is "go global in minutes".
> - D: That is elasticity.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q3
An application must continue processing transactions with no interruption at all if a server or an Availability Zone fails. Which design characteristic does this describe?

- A. Elasticity
- B. Agility
- C. Fault tolerance
- D. Scalability

> [!success]- Answer
> **C.** Fault tolerance means the system keeps operating without interruption when components fail.
> - A: Elasticity matches resources to demand; it is not about surviving failures.
> - B: Agility is the speed of provisioning and innovation.
> - D: Scalability is the ability to grow to handle more load.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q4
A development team used to wait six weeks for new test servers. After moving to AWS, the team creates test environments in minutes and deletes them after each experiment. Which benefit of the AWS Cloud does this demonstrate?

- A. Increased speed and agility
- B. High availability
- C. Economies of scale
- D. Fault tolerance

> [!success]- Answer
> **A.** Reducing the time to obtain resources from weeks to minutes, so teams can experiment cheaply, is the AWS definition of increased speed and agility.
> - B: High availability is about uptime during failures.
> - C: Economies of scale concern lower prices from AWS's size.
> - D: Fault tolerance is about continuing without interruption when components fail.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q5
Which TWO of the following are benefits of AWS global infrastructure? (Select TWO.)

- A. Customers can deploy applications close to end users in many parts of the world to reduce latency.
- B. Customers receive physical access to AWS data centers for audits.
- C. Customers can launch resources in a new geographic area in minutes without building facilities.
- D. Customers no longer need to configure security for their applications.
- E. All AWS services are available in every Region on launch day.

> [!success]- Answer
> **A and C.** Global reach (low latency near users) and speed of deployment are the global infrastructure benefits named in the exam guide.
> - B: AWS does not give customers physical data center access; compliance reports come from AWS Artifact.
> - D: Customers remain responsible for security in the cloud.
> - E: Service availability varies by Region.
>
> Review: [[1.1 Benefits of the AWS Cloud]]

### Q6
A solutions team is reviewing a workload and decides to replace one large EC2 instance with several smaller instances spread across Availability Zones, so that one failure has less impact. Which Well-Architected pillar does this design principle belong to?

- A. Performance efficiency
- B. Reliability
- C. Cost optimization
- D. Operational excellence

> [!success]- Answer
> **B.** "Scale horizontally to increase aggregate workload availability" is a reliability design principle.
> - A: Performance efficiency concerns choosing efficient resources for speed, not reducing failure impact.
> - C: The change is driven by resilience, not cost.
> - D: Operational excellence concerns operating procedures and processes.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q7
A company wants to reduce the energy consumed by its cloud workloads by increasing server utilization and adopting more efficient instance types as they are released. Which pillar of the AWS Well-Architected Framework is the company focusing on?

- A. Cost optimization
- B. Performance efficiency
- C. Sustainability
- D. Reliability

> [!success]- Answer
> **C.** The stated goal is reducing energy use and environmental impact, which is the sustainability pillar (principles: maximize utilization; anticipate and adopt more efficient hardware and software).
> - A: Cost optimization would be correct if the goal were spending less money.
> - B: Performance efficiency focuses on meeting requirements efficiently, not energy.
> - D: Reliability is about consistent operation and recovery.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q8
A company wants to evaluate an existing workload against AWS best practices by answering a set of questions about each pillar, and receive a list of high-risk issues and an improvement plan. Which AWS service should it use?

- A. AWS Trusted Advisor
- B. AWS Well-Architected Tool
- C. AWS Config
- D. Amazon Inspector

> [!success]- Answer
> **B.** The AWS Well-Architected Tool is a free, questionnaire-based review of a workload against the six pillars that outputs risks and an improvement plan.
> - A: Trusted Advisor runs automated checks against resources in the account; it does not use pillar questionnaires.
> - C: AWS Config records resource configurations and evaluates them against rules.
> - D: Amazon Inspector scans workloads for software vulnerabilities.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q9
Which TWO design principles belong to the operational excellence pillar of the AWS Well-Architected Framework? (Select TWO.)

- A. Perform operations as code
- B. Implement a strong identity foundation
- C. Make frequent, small, reversible changes
- D. Democratize advanced technologies
- E. Adopt a consumption model

> [!success]- Answer
> **A and C.** Both are operational excellence design principles (current wording also includes "safely automate where possible").
> - B: Security pillar.
> - D: Performance efficiency pillar.
> - E: Cost optimization pillar.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q10
A company is selecting the Amazon EC2 instance family and storage type that give its analytics application the lowest query response time. Which Well-Architected pillar is MOST relevant?

- A. Performance efficiency
- B. Reliability
- C. Security
- D. Sustainability

> [!success]- Answer
> **A.** Selecting the right resource types and sizes to meet performance requirements is performance efficiency.
> - B: Reliability is about consistent operation and recovering from failure.
> - C: Security is about protecting data and systems.
> - D: Sustainability is about environmental impact.
>
> Review: [[1.2 Design Principles - Well-Architected Framework]]

### Q11
A company's leadership is concerned that employees lack the skills to work with AWS. It plans training programs and a strategy to change its organizational culture. Which AWS Cloud Adoption Framework (AWS CAF) perspective addresses these concerns?

- A. Governance
- B. Operations
- C. People
- D. Business

> [!success]- Answer
> **C.** The People perspective covers cloud fluency, workforce transformation, culture evolution, and change acceleration.
> - A: Governance covers program management, risk, benefits, and cloud financial management.
> - B: Operations covers observability, incident, patch, and change management.
> - D: Business covers strategy, portfolio, innovation, and product management.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q12
Which AWS CAF perspective includes cloud financial management and risk management capabilities, with stakeholders such as the CFO and chief risk officer?

- A. Business
- B. Governance
- C. Security
- D. Platform

> [!success]- Answer
> **B.** The Governance perspective includes program and project management, benefits management, risk management, and cloud financial management.
> - A: Business perspective covers strategy, portfolio, and innovation management; the CFO is a stakeholder there too, but risk and cloud financial management are Governance capabilities.
> - C: Security covers security governance, threat detection, and data protection.
> - D: Platform covers architecture, engineering, and CI/CD.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q13
During its cloud transformation, a company has identified capability gaps across the six AWS CAF perspectives and is building strategies to improve cloud readiness. Which AWS CAF transformation phase is the company in?

- A. Envision
- B. Align
- C. Launch
- D. Scale

> [!success]- Answer
> **B.** The Align phase identifies capability gaps across the six perspectives, cross-organizational dependencies, and stakeholder concerns.
> - A: Envision identifies and prioritizes transformation opportunities tied to business outcomes.
> - C: Launch delivers pilot initiatives in production.
> - D: Scale expands pilots to full production and sustains benefits.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q14
A company moves its on-premises Oracle database to Amazon RDS for Oracle so that AWS handles patching and backups. The application code is not changed. Which migration strategy is this?

- A. Rehost
- B. Replatform
- C. Refactor
- D. Repurchase

> [!success]- Answer
> **B.** Moving to a managed service for some optimization without changing the core application is replatform ("lift, tinker, and shift").
> - A: Rehost would move the database server as-is (for example, onto EC2) with no platform change.
> - C: Refactor would redesign the application for cloud-native features.
> - D: Repurchase would replace the product with a different one.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q15
A research institute must move 4 PB of archived data from a remote facility with a slow internet connection to Amazon S3. Which AWS option is MOST appropriate for this migration?

- A. AWS Database Migration Service (AWS DMS)
- B. AWS Snow Family
- C. AWS Application Migration Service
- D. AWS Transfer Family

> [!success]- Answer
> **B.** Snow Family devices move very large datasets offline when network transfer would be too slow.
> - A: DMS migrates databases over the network.
> - C: Application Migration Service rehosts servers, not bulk archives.
> - D: Transfer Family provides SFTP/FTPS/FTP endpoints over the network, which would still be limited by the slow link.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q16
A company wants to migrate a production MySQL database to Amazon Aurora with minimal downtime. The source database must remain available to users during the migration. Which service should it use?

- A. AWS Database Migration Service (AWS DMS)
- B. AWS Snowball Edge
- C. AWS Migration Hub
- D. AWS Application Discovery Service

> [!success]- Answer
> **A.** AWS DMS keeps the source database operational and uses ongoing replication to keep the target in sync until cutover.
> - B: Snowball Edge is for offline bulk transfer, which would require downtime to stay consistent.
> - C: Migration Hub tracks migrations but does not move data.
> - D: Application Discovery Service collects data for planning; it does not migrate.
>
> Review: [[1.3 Migration Strategies and AWS CAF]]

### Q17
Which TWO of the following are costs of an on-premises data center that are reduced or eliminated by moving workloads to AWS? (Select TWO.)

- A. Power and cooling for server rooms
- B. Designing the application's database schema
- C. Hardware refresh every few years
- D. Managing IAM permissions for users
- E. Writing application code

> [!success]- Answer
> **A and C.** Facilities (power, cooling) and hardware purchase and refresh are on-premises costs that AWS absorbs.
> - B: Schema design remains the customer's job.
> - D: Identity and access configuration is a customer responsibility in the cloud.
> - E: Application code is still written by the customer.
>
> Review: [[1.4 Cloud Economics]]

### Q18
A company runs Amazon EC2 instances that average 8% CPU utilization. It wants to lower costs by moving to instance sizes that match the actual workload. What is this practice called, and which service can recommend the new sizes?

- A. Elasticity; AWS Auto Scaling
- B. Rightsizing; AWS Compute Optimizer
- C. Reserved capacity; AWS Budgets
- D. Replatforming; AWS Application Migration Service

> [!success]- Answer
> **B.** Matching instance size to actual utilization is rightsizing, and AWS Compute Optimizer recommends optimal instance types and sizes.
> - A: Elasticity changes the number of resources as demand changes; it does not fix oversized instances.
> - C: Reserved capacity changes how you pay, and AWS Budgets only alerts on spending.
> - D: Replatforming is a migration strategy.
>
> Review: [[1.4 Cloud Economics]]

### Q19
A company already owns Microsoft Windows Server licenses with terms that require them to be assigned to physical cores. It wants to reuse these licenses on AWS. Which combination meets this need?

- A. License-included Amazon EC2 instances on Spot Instances
- B. Bring Your Own License (BYOL) on Amazon EC2 Dedicated Hosts
- C. AWS Marketplace subscription with On-Demand Instances
- D. License-included Amazon RDS with Reserved Instances

> [!success]- Answer
> **B.** BYOL reuses existing licenses, and Dedicated Hosts provide visibility into physical cores and sockets for core-based license terms.
> - A: License-included pricing means paying for a new license, not reusing the existing one.
> - C: A Marketplace subscription is a new purchase.
> - D: License included again means paying AWS for the license.
>
> Review: [[1.4 Cloud Economics]]

### Q20
A company must deploy the same networking, compute, and database setup in three AWS Regions, and wants every deployment to be identical, repeatable, and version-controlled. Which approach meets these requirements?

- A. Use the AWS Management Console to create resources in each Region by following a written checklist.
- B. Define the infrastructure in AWS CloudFormation templates and deploy stacks in each Region.
- C. Use AWS License Manager to copy resources between Regions.
- D. Use AWS Trusted Advisor to create the resources automatically.

> [!success]- Answer
> **B.** CloudFormation infrastructure as code provides repeatable, consistent, version-controlled provisioning across Regions and accounts.
> - A: Manual console work is error-prone and not repeatable.
> - C: License Manager tracks software licenses; it does not provision resources.
> - D: Trusted Advisor makes recommendations; it does not provision infrastructure.
>
> Review: [[1.4 Cloud Economics]]
