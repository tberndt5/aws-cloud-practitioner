---
tags:
  - clf-c02
  - services
  - services/management-and-governance
category: "Management and Governance"
status: not-started
---
# Services: Management and Governance

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

This is one of the most heavily tested categories because so many of its services sound alike. Concepts live in the task notes: governance and logging in [[2.2 Security, Governance, and Compliance Concepts]], Trusted Advisor as a security tool in [[2.4 Security Components and Resources]], ways to provision and operate (console, IaC) in [[3.1 Deploying and Operating in the AWS Cloud]], Organizations and consolidated billing in [[4.2 Billing, Budget, and Cost Management]], and Trusted Advisor and AWS Health in [[4.3 Technical Resources and Support Options]].

| Service | What it is | Cue in a question |
|---|---|---|
| [[#AWS Auto Scaling]] | Scaling plans across several resource types | "scale EC2, ECS, DynamoDB, and Aurora together" |
| [[#AWS CloudFormation]] | Infrastructure as code with templates | "template", "repeatable", "provision the same stack in many Regions" |
| [[#AWS CloudTrail]] | Log of API calls and user actions | "who did what, when", "audit API activity" |
| [[#Amazon CloudWatch]] | Metrics, logs, alarms, dashboards | "CPU utilization", "alarm", "monitor performance" |
| [[#AWS Compute Optimizer]] | ML rightsizing recommendations for compute | "over-provisioned EC2", "right instance size" |
| [[#AWS Config]] | Resource configuration history and compliance rules | "configuration changed", "is this resource compliant over time" |
| [[#AWS Control Tower]] | Set up and govern a multi-account landing zone | "landing zone", "best-practice multi-account setup quickly" |
| [[#AWS Health Dashboard]] | AWS service and account event status | "AWS outage affecting my resources", "scheduled maintenance" |
| [[#AWS Launch Wizard]] | Guided deployment of apps like SQL Server, SAP | "deploy SAP or SQL Server following AWS best practices" |
| [[#AWS License Manager]] | Track and enforce software licenses | "BYOL", "license count", "Microsoft or Oracle licenses" |
| [[#AWS Management Console]] | Web interface for AWS | "browser", "point-and-click" |
| [[#AWS Organizations]] | Central multi-account management and billing | "consolidated billing", "SCP", "OUs" |
| [[#AWS Resource Groups and Tag Editor]] | Group and bulk-tag resources | "tag many resources at once", "view resources by tag" |
| [[#AWS Service Catalog]] | Catalog of IT-approved products | "users may launch only approved products" |
| [[#AWS Systems Manager]] | Operate and patch fleets of servers | "patch", "run commands on many instances", "shell without SSH" |
| [[#AWS Trusted Advisor]] | Best-practice checks on your account | "recommendations for cost, security, limits" |
| [[#AWS Well-Architected Tool]] | Review a workload against the six pillars | "review my architecture against Well-Architected" |

> [!tip] The three-way monitoring split
> **CloudWatch** = how is it performing (metrics, alarms). **CloudTrail** = who did it (API calls). **Config** = what does it look like and did it change or drift from rules (resource configuration).

## AWS Auto Scaling

> [!summary] Monitors applications to automatically scale resources dynamically by adjusting capacity based on defined thresholds.

- **What it does:** Lets you build scaling plans that scale several related resources together from one place. It covers Amazon EC2 Auto Scaling groups, Spot Fleets, Amazon ECS tasks, DynamoDB table and index capacity, and Aurora read replicas.
- **Choose it when:** The question wants one service to scale multiple resource types (not only EC2) for an application, or asks which service provides elasticity based on demand.
- **Key facts:**
  - Auto scaling is the exam's core example of **elasticity**: add capacity when demand rises, remove it when it falls.
  - Uses CloudWatch metrics and target values (for example, keep CPU at 50%).
  - Scaling plans can optimize for availability, cost, or a balance of both, and support predictive scaling.
  - No extra charge; you pay for CloudWatch and the resources launched.
- **Don't confuse with:** [[Services - Compute#Amazon EC2 Auto Scaling|Amazon EC2 Auto Scaling]], which adds and removes EC2 instances in one Auto Scaling group; AWS Auto Scaling coordinates scaling across several services. [[Services - Compute#Elastic Load Balancing (ELB)|Elastic Load Balancing]] spreads traffic but does not add capacity.
- **Docs:** [What is a scaling plan? (AWS Auto Scaling User Guide)](https://docs.aws.amazon.com/autoscaling/plans/userguide/what-is-a-scaling-plan.html)

## AWS CloudFormation

> [!summary] Model, set up, and create templates of AWS resources.

- **What it does:** Infrastructure as code (IaC). You describe resources in a JSON or YAML **template**, and CloudFormation creates, updates, and deletes them together as a **stack** in the right order.
- **Choose it when:** The scenario asks for repeatable, consistent, automated provisioning; deploying identical environments across Regions or accounts; version-controlling infrastructure; or quickly rebuilding an environment after a disaster.
- **Key facts:**
  - The exam guide uses CloudFormation as the example of automation benefits: fewer manual errors, speed, consistency.
  - CloudFormation itself is free; you pay for the resources it creates.
  - Stack updates can be previewed with change sets; drift detection shows manual changes made outside the template.
  - StackSets deploy one stack across multiple accounts and Regions.
- **Don't confuse with:** [[Services - Compute#AWS Elastic Beanstalk|Elastic Beanstalk]] (you upload application code and it builds the environment for you; CloudFormation provisions any infrastructure you define). [[#AWS Service Catalog]] publishes approved CloudFormation templates for others to launch. [[#AWS Config]] records configuration; it does not provision.
- **Docs:** [What is AWS CloudFormation?](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

## AWS CloudTrail

> [!summary] Records actions taken by users in the console, AWS CLI, AWS SDKs, and APIs.

- **What it does:** Logs API activity in your account: which identity made which call, from which IP address, at what time, and whether it succeeded. It is the audit trail for "who did what".
- **Choose it when:** The question asks who deleted, changed, or launched a resource; asks for an audit log of account activity; or asks where to find logs for a security investigation.
- **Key facts:**
  - Enabled by default; **Event history** shows the last ==90 days== of management events at no charge.
  - Create a **trail** to keep events longer by delivering them to an Amazon S3 bucket (optionally also to CloudWatch Logs).
  - Records management events (control-plane actions such as `RunInstances`) and, if enabled, data events (such as S3 object reads).
  - An organization trail can log every account in AWS Organizations.
  - CloudTrail logs are a data source for GuardDuty and Detective.
- **Don't confuse with:** [[#Amazon CloudWatch]] measures performance (CPU, latency) and raises alarms, not who made a call. [[#AWS Config]] records what a resource's configuration was and whether it complies; CloudTrail records the API call that changed it.
- **Docs:** [What is AWS CloudTrail?](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)

## Amazon CloudWatch

> [!summary] Monitors resources and applications, collects and tracks metrics, has alarms.

- **What it does:** Collects metrics and logs from AWS resources and your applications, shows them on dashboards, and triggers alarms when thresholds are crossed. Alarms can notify through Amazon SNS or take actions such as scaling or stopping an instance.
- **Choose it when:** The scenario mentions CPU utilization, performance metrics, application logs, a dashboard of resource health, or "alert me when a metric exceeds a value". The exam guide cites CloudWatch as the monitoring example in governance.
- **Key facts:**
  - Main parts: **Metrics**, **Alarms**, **Logs** (CloudWatch Logs), **Dashboards**.
  - Many AWS services publish metrics automatically; memory and disk-space usage on EC2 need the CloudWatch agent.
  - Billing alarms on estimated charges are a CloudWatch feature (AWS Budgets is the fuller budgeting tool).
  - Alarms drive EC2 Auto Scaling policies.
- **Don't confuse with:** [[#AWS CloudTrail]] (who called which API). [[#AWS Config]] (configuration state and compliance). [[Services - Developer Tools#AWS X-Ray|AWS X-Ray]] traces individual requests through a distributed application. [[Services - Application Integration#Amazon EventBridge|Amazon EventBridge]] routes events (it grew out of CloudWatch Events).
- **Docs:** [What is Amazon CloudWatch?](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)

## AWS Compute Optimizer

> [!summary] Analyzes the configuration and utilization metrics of resources, provides optimization recommendations.

- **What it does:** Uses machine learning on historical utilization metrics to recommend the right size and type for compute resources, flagging what is over-provisioned (wasting money) or under-provisioned (hurting performance).
- **Choose it when:** The question is about **rightsizing**: choosing the best EC2 instance type or size, Lambda memory size, or EBS volume type from actual usage.
- **Key facts:**
  - Covers EC2 instances, EC2 Auto Scaling groups, EBS volumes, Lambda functions, ECS services on Fargate, and more.
  - Reads CloudWatch metrics; by default analyzes the last 14 days of metrics.
  - Free to opt in for its standard recommendations.
- **Don't confuse with:** [[#AWS Trusted Advisor]] gives broad best-practice checks across cost, security, performance, fault tolerance, service limits, and operational excellence; Compute Optimizer gives deep, compute-specific sizing recommendations. [[Services - Cost Management#AWS Cost Explorer|Cost Explorer]] shows spending trends, not instance-size advice.
- **Docs:** [What is AWS Compute Optimizer?](https://docs.aws.amazon.com/compute-optimizer/latest/ug/what-is-compute-optimizer.html)

## AWS Config

> [!summary] Provides a detailed view of AWS resource configuration, changes in configuration, and compliance.

- **What it does:** Continuously records the configuration of your resources and keeps a history of every change. **Config rules** evaluate resources against desired settings and mark them compliant or noncompliant.
- **Choose it when:** The question asks what a resource looked like at a past point in time, wants to track configuration changes, or wants continuous compliance checks such as "flag any S3 bucket that allows public access" or "all EBS volumes must be encrypted". The exam guide lists Config as an auditing service.
- **Key facts:**
  - Managed rules (prebuilt) and custom rules; conformance packs bundle rules for a standard.
  - Can trigger automatic remediation through Systems Manager Automation.
  - Regional service; an aggregator can combine data across accounts and Regions.
  - Security Hub uses Config rules for many of its checks.
- **Don't confuse with:** [[#AWS CloudTrail]] records the API call and caller; Config records the resulting resource state and compliance. [[Services - Security, Identity, and Compliance#AWS Audit Manager|Audit Manager]] collects evidence for auditors against frameworks and can pull Config results as evidence. [[#AWS Trusted Advisor]] checks a fixed list of AWS best practices; Config evaluates rules you choose.
- **Docs:** [What is AWS Config?](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)

## AWS Control Tower

> [!summary] Set up and govern a multi-account environment.

- **What it does:** Builds a well-architected multi-account **landing zone** in a short time using best practices, then keeps it governed. It orchestrates AWS Organizations, IAM Identity Center, and Service Catalog for you.
- **Choose it when:** A company wants to quickly set up a new, secure multi-account environment following AWS best practices, with automated account provisioning and ongoing guardrails, without wiring Organizations together by hand.
- **Key facts:**
  - **Landing zone**: the baseline multi-account environment (OUs, log archive account, audit account).
  - **Controls** (also called **guardrails**): preventive (block actions, implemented with SCPs), detective (detect noncompliance, implemented with Config rules), and proactive (check resources before they are provisioned).
  - **Account Factory**: a template for provisioning new accounts with pre-approved settings.
  - A dashboard shows noncompliant resources across accounts.
- **Don't confuse with:** [[#AWS Organizations]] is the underlying account-grouping, SCP, and consolidated-billing service you configure yourself; Control Tower automates a best-practice setup on top of it. [[#AWS Service Catalog]] controls which products users can launch inside an account.
- **Docs:** [What is AWS Control Tower?](https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html)

## AWS Health Dashboard

> [!summary] Provides ongoing visibility into resource performance and availability of AWS services and user accounts.

- **What it does:** Shows the status of AWS services and the events that affect your own account and resources, such as outages, scheduled maintenance, and required actions, with guidance for each event.
- **Choose it when:** The question asks how to learn whether an AWS-side issue is affecting your resources, or how to be notified of upcoming maintenance on your EC2 instances or other resources.
- **Key facts:**
  - **Service health** view: the public status of all AWS services in all Regions, the same for every customer.
  - **Your account health** view: personalized events that affect your resources (formerly the Personal Health Dashboard).
  - Free for all customers and requires no setup; events can be sent to Amazon EventBridge for automated alerts.
  - The **AWS Health API** (programmatic access) requires Business, Enterprise On-Ramp, or Enterprise Support.
- **Don't confuse with:** [[#Amazon CloudWatch]] monitors the health and metrics of **your** resources and applications; Health Dashboard reports **AWS-side** events. [[#AWS Trusted Advisor]] gives best-practice recommendations, not outage notices.
- **Docs:** [What is AWS Health?](https://docs.aws.amazon.com/health/latest/ug/what-is-aws-health.html)
- Current status: the AWS Health page now lists Business Support+, Enterprise, and Unified Operations as the plans for the Health API, with Business and Enterprise On-Ramp still accepted until customers transition. For the exam, use Business, Enterprise On-Ramp, or Enterprise.

## AWS Launch Wizard

> [!summary] Deploy application and domain-controller solutions to the cloud.

- **What it does:** A guided console wizard that sizes, configures, and deploys third-party applications on AWS following AWS best practices, such as Microsoft SQL Server, SAP systems, and Active Directory domain controllers.
- **Choose it when:** A team wants to deploy a complex packaged application such as SAP or SQL Server on AWS without designing the infrastructure itself.
- **Key facts:**
  - You enter application requirements; Launch Wizard recommends resources, estimates cost, and provisions them.
  - It produces reusable CloudFormation templates.
  - No extra charge; you pay for the resources deployed.
- **Don't confuse with:** [[#AWS CloudFormation]] deploys whatever you define in a template; Launch Wizard is an application-specific guided front end. [[#AWS Service Catalog]] offers products your own IT team approved.
- **Docs:** [What is AWS Launch Wizard?](https://docs.aws.amazon.com/launchwizard/latest/userguide/what-is-launch-wizard.html)

## AWS License Manager

> [!summary] Manage software licenses from software vendors centrally across AWS and on-premises environments.

- **What it does:** Tracks license usage for software from vendors such as Microsoft, Oracle, IBM, and SAP. You define licensing rules (for example, number of vCPUs or cores), and License Manager can block launches that would break them.
- **Choose it when:** The scenario involves Bring Your Own License (BYOL), tracking license counts, or avoiding license-compliance violations and audit penalties.
- **Key facts:**
  - Works across AWS and on-premises servers.
  - Supports Dedicated Hosts for licenses tied to physical cores or sockets.
  - Ties to the exam's BYOL versus license-included topic in [[1.4 Cloud Economics]].
- **Don't confuse with:** [[Services - Cost Management#AWS Marketplace|AWS Marketplace]] is where you buy software (including license-included products); License Manager tracks licenses you own. [[#AWS Config]] tracks resource configuration, not license counts.
- **Docs:** [What is AWS License Manager?](https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager.html)

## AWS Management Console

> [!summary] Web application used to manage AWS resources.

- **What it does:** The browser-based graphical interface for signing in and managing AWS services. The AWS Console Mobile Application gives limited access from a phone.
- **Choose it when:** The scenario describes a one-time task, a visual or point-and-click workflow, or a non-technical user exploring services.
- **Key facts:**
  - One of the three access methods: Console, programmatic (CLI, SDKs, APIs), and infrastructure as code.
  - Good for one-off actions and learning; poor for repeatable work, which favors scripts or IaC.
  - Sign-in uses the root user, IAM users, or IAM Identity Center; console access should use MFA.
  - AWS CloudShell launches a pre-authenticated shell from inside the console.
- **Don't confuse with:** [[Services - Developer Tools#AWS CLI|AWS CLI]] and [[Services - Developer Tools#AWS SDKs|AWS SDKs]] (programmatic, scriptable). [[#AWS CloudFormation]] (repeatable IaC).
- **Docs:** [What is the AWS Management Console?](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/what-is.html)

## AWS Organizations

> [!summary] Account management service that can consolidate billing and accounts.

- **What it does:** Groups multiple AWS accounts under one management account, arranges them into organizational units (OUs), applies policies centrally, and pays one combined bill.
- **Choose it when:** The question mentions consolidated billing, one bill for many accounts, volume discounts across accounts, restricting what member accounts can do, or creating accounts programmatically.
- **Key facts:**
  - **Consolidated billing**: one payment method; usage is combined across accounts for volume pricing tiers; Reserved Instance and Savings Plans discounts can be shared across accounts. No extra charge.
  - **Service control policies (SCPs)** set the maximum permissions for accounts or OUs. They do not grant permissions, and they also restrict the member account's root user.
  - Hierarchy: root, OUs (can be nested), accounts.
  - The management account pays the bill; member accounts are linked to it.
- **Don't confuse with:** [[#AWS Control Tower]] sets up a best-practice landing zone on top of Organizations. IAM policies grant permissions to users and roles inside one account; SCPs cap what an entire account can do. [[Services - Security, Identity, and Compliance#AWS Resource Access Manager (AWS RAM)|AWS RAM]] shares specific resources between accounts.
- **Docs:** [What is AWS Organizations?](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)

## AWS Resource Groups and Tag Editor

> [!summary] Organize AWS resources into groups by tag or CloudFormation stack, and add or edit tags on many resources at once.

- **What it does:** **Resource Groups** collects resources that share tags or belong to the same CloudFormation stack so you can view and act on them as one unit. **Tag Editor** finds resources across Regions and services and adds, edits, or removes tags in bulk.
- **Choose it when:** The question asks how to tag many existing resources at once, find all resources with a given tag, or manage resources for one application or environment together.
- **Key facts:**
  - A tag is a key-value pair such as `Environment=Production`.
  - Consistent tagging supports cost allocation tags in billing reports, automation, and access control.
  - Systems Manager can run operations against a resource group.
- **Don't confuse with:** Cost allocation tags (activated in the Billing console to break down costs, see [[4.2 Billing, Budget, and Cost Management]]); Tag Editor applies the tags, billing uses them. [[#AWS Organizations]] groups accounts, not resources.
- **Docs:** [What are resource groups?](https://docs.aws.amazon.com/ARG/latest/userguide/resource-groups.html)

## AWS Service Catalog

> [!summary] Create and manage catalogs of IT services that are approved for AWS.

- **What it does:** Administrators publish approved **products** (defined as CloudFormation templates) into **portfolios**. Users can launch only those products, with the configurations and permissions IT allowed.
- **Choose it when:** A company wants users or developers to self-serve resources, but only from a pre-approved, compliant list, for governance and consistency.
- **Key facts:**
  - Products are built from CloudFormation templates; portfolios control who can see which products.
  - Launch constraints let users deploy products without having broad IAM permissions themselves.
  - Control Tower's Account Factory is built on Service Catalog.
- **Don't confuse with:** [[Services - Cost Management#AWS Marketplace|AWS Marketplace]] is a public catalog of third-party software you buy; Service Catalog is your organization's internal list of approved products. [[#AWS Control Tower]] governs multiple accounts. [[#AWS Organizations]] SCPs restrict actions; they do not offer a menu of approved products.
- **Docs:** [What is AWS Service Catalog?](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/introduction.html)

## AWS Systems Manager

> [!summary] Organize, monitor, and automate management tasks on AWS resources.

- **What it does:** A collection of tools for operating fleets of EC2 instances and on-premises servers (managed nodes) from one place: patching, running commands, remote access, configuration, and inventory.
- **Choose it when:** The question involves patching many servers, running a script on a fleet, secure shell access without opening ports, storing configuration values, or managing hybrid (on-premises plus AWS) servers.
- **Key facts:** recognize these capabilities by name:
  - **Session Manager**: browser or CLI shell access to instances with no SSH keys, no bastion host, and no inbound port 22; sessions can be logged.
  - **Parameter Store**: stores configuration data and secrets (plain text or encrypted with KMS); the exam guide names Systems Manager for credential storage.
  - **Patch Manager**: automates OS and application patching on a schedule.
  - **Run Command**: runs commands or scripts on many instances at once.
  - Also: Automation (runbooks), Inventory, OpsCenter, State Manager.
  - Works on EC2 and on-premises servers through the SSM Agent.
- **Don't confuse with:** [[Services - Security, Identity, and Compliance#AWS Secrets Manager|Secrets Manager]] has built-in automatic rotation of secrets such as database passwords; Parameter Store is cheaper general configuration storage without built-in rotation. [[#AWS Config]] records configuration; Systems Manager acts on instances. [[Services - Security, Identity, and Compliance#Amazon Inspector|Amazon Inspector]] finds vulnerabilities; Patch Manager fixes them.
- **Docs:** [What is AWS Systems Manager?](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)

## AWS Trusted Advisor

> [!summary] Inspects a user's AWS environment and makes recommendations based on best practices.

- **What it does:** Runs automated checks on your account and recommends improvements, such as idle resources to delete, security groups with unrestricted ports, missing root MFA, or services nearing their quotas.
- **Choose it when:** The question asks for best-practice recommendations across cost, security, performance, fault tolerance, or service limits, or which tool identifies security issues such as open ports or public snapshots (exam guide task 2.4).
- **Key facts:**
  - Check categories: ==cost optimization, performance, security, fault tolerance, service limits (quotas)==, and operational excellence.
  - **Basic and Developer** Support get the core checks: service quotas plus basic security checks (for example, S3 bucket permissions, security groups with specific ports unrestricted, root MFA, public EBS and RDS snapshots).
  - **Business, Enterprise On-Ramp, and Enterprise** Support get all checks plus programmatic access through the API.
  - Recommendations only; it does not fix things automatically.
- **Don't confuse with:** [[#AWS Compute Optimizer]] (deep ML rightsizing for compute only). [[#AWS Well-Architected Tool]] (a question-based review of one workload's design, which you run). [[Services - Security, Identity, and Compliance#Amazon Inspector|Amazon Inspector]] scans workloads for software vulnerabilities (CVEs); Trusted Advisor checks account configuration. [[#AWS Config]] evaluates rules you define.
- **Docs:** [AWS Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html)
- Current status: AWS has announced that the Developer, Business, and Enterprise On-Ramp Support plans end on January 1, 2027 (replaced by Business Support+ and Enterprise), per the [Trusted Advisor check reference](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor-check-reference.html). The exam still uses the five-plan model above.

## AWS Well-Architected Tool

> [!summary] Provides recommendations to improve workloads based on best practices.

- **What it does:** A free console tool in which you answer questions about a specific workload; it compares your answers with the AWS Well-Architected Framework's six pillars, highlights high- and medium-risk issues, and gives an improvement plan.
- **Choose it when:** The scenario asks how to review an architecture against the Well-Architected Framework or measure a workload against its pillars over time.
- **Key facts:**
  - Pillars: operational excellence, security, reliability, performance efficiency, cost optimization, sustainability (see [[1.2 Design Principles - Well-Architected Framework]]).
  - Lenses add domain-specific questions (for example, Serverless or SaaS lenses).
  - Free; you record milestones to track progress.
- **Don't confuse with:** [[#AWS Trusted Advisor]] scans your account automatically; the Well-Architected Tool is a self-assessment questionnaire about a workload's design. The Framework itself (see [[Well-Architected and CAF]]) is the guidance; the Tool applies it.
- **Docs:** [What is the AWS Well-Architected Tool?](https://docs.aws.amazon.com/wellarchitected/latest/userguide/intro.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
