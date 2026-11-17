---
tags:
  - clf-c02
  - practice
  - domain-2
---
# Practice - Domain 2: Security and Compliance

25 original exam-style questions. Answer each before opening the callout. Questions 1 to 6 cover 2.1, 7 to 13 cover 2.2, 14 to 20 cover 2.3, and 21 to 25 cover 2.4.

### Q1
A company runs a web application on Amazon EC2 instances. Under the AWS shared responsibility model, which task is the company's responsibility?

- A. Maintaining the physical hosts that run the instances
- B. Applying security patches to the instances' guest operating system
- C. Securing the hypervisor that isolates the instances
- D. Replacing failed storage hardware in the Availability Zone

> [!success]- Answer
> **B.** "Patch OS of EC2 instances" and "manage guest OS" are customer responsibilities for IaaS.
> - A: Hosts are an AWS responsibility.
> - C: "Secure the EC2 hypervisor" is on the AWS list.
> - D: Hardware maintenance is AWS's job.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q2
A company migrates its self-managed MySQL database from Amazon EC2 to Amazon RDS for MySQL. Which responsibility shifts from the company to AWS?

- A. Managing database user accounts and their privileges
- B. Configuring the security group that controls access to the database
- C. Patching the operating system that the database runs on
- D. Deciding whether the data should be encrypted at rest

> [!success]- Answer
> **C.** "Patch OS of RDS instances" is an AWS responsibility because RDS is a managed service; on EC2 the customer patched it.
> - A: Database users and permissions stay with the customer.
> - B: Firewall (security group) configuration stays with the customer.
> - D: Encryption choices stay with the customer.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q3
Which of the following are shared responsibilities between AWS and the customer? (Select TWO.)

- A. Configuration management
- B. Physical and environmental controls
- C. Awareness and training
- D. Client-side data encryption
- E. Edge location management

> [!success]- Answer
> **A and C.** Patches, configuration, and training and awareness are the shared items; each party handles its own layer and its own staff.
> - B: An inherited control, fully AWS.
> - D: A customer responsibility.
> - E: An AWS responsibility.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q4
A team deploys an application as AWS Lambda functions. Which task remains the team's responsibility?

- A. Patching the operating system used by Lambda
- B. Scaling the underlying servers when requests increase
- C. Managing the IAM permissions granted to the function
- D. Maintaining the runtime environment's host hardware

> [!success]- Answer
> **C.** With serverless, the customer still owns code, data, and IAM permissions such as the execution role.
> - A: "Patch OS used by Lambda" is on the AWS list.
> - B: Lambda scales automatically; AWS manages the servers.
> - D: Hardware is always AWS's.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q5
A security auditor asks how physical security controls at AWS data centers apply to a company's workloads. Which type of control are these for the company?

- A. Inherited controls
- B. Shared controls
- C. Customer-specific controls
- D. Compensating controls

> [!success]- Answer
> **A.** Physical and environmental controls are inherited: the customer fully inherits them from AWS.
> - B: Shared controls (patching, configuration, training) involve both parties.
> - C: Customer-specific controls, such as zone security, belong only to the customer.
> - D: Not a category in the AWS shared responsibility model.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q6
A company stores customer records in Amazon DynamoDB. Under the shared responsibility model, which task is the company's responsibility?

- A. Managing the servers that host DynamoDB tables
- B. Replicating data across storage hardware within the Region
- C. Patching the DynamoDB database software
- D. Determining which applications and services have access to the tables

> [!success]- Answer
> **D.** "Determine which services have access to DynamoDB tables" is a customer item; IAM permissions and data stay with the customer even for fully managed services.
> - A: AWS operates the infrastructure for DynamoDB.
> - B: AWS manages the underlying storage and replication.
> - C: AWS patches the managed service software.
>
> Review: [[2.1 Shared Responsibility Model]]

### Q7
A healthcare company must give its auditors AWS's ISO 27001 certification and SOC 2 report. Where can the company download these documents?

- A. AWS Audit Manager
- B. AWS Security Hub
- C. AWS Artifact
- D. AWS Trusted Advisor

> [!success]- Answer
> **C.** AWS Artifact gives on-demand access to AWS security and compliance reports.
> - A: Audit Manager collects evidence about the customer's own usage, not AWS's reports.
> - B: Security Hub aggregates security findings.
> - D: Trusted Advisor gives best-practice recommendations.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q8
An administrator needs to find out which IAM user deleted an Amazon S3 bucket last week. Which service provides this information?

- A. Amazon CloudWatch
- B. Amazon Inspector
- C. AWS Config
- D. AWS CloudTrail

> [!success]- Answer
> **D.** CloudTrail records API calls with the identity, time, and source of each action.
> - A: CloudWatch handles metrics, logs, and alarms, not who made API calls.
> - B: Inspector scans for vulnerabilities.
> - C: Config records configuration state and changes, not the identity behind the call as its main purpose.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q9
A company wants to be alerted when any Amazon EBS volume is created without encryption and to keep a history of how each volume's settings changed over time. Which service meets these requirements?

- A. AWS Config
- B. AWS CloudTrail
- C. Amazon GuardDuty
- D. AWS Artifact

> [!success]- Answer
> **A.** Config records configuration history and evaluates resources against rules such as "EBS volumes must be encrypted".
> - B: CloudTrail logs API calls but does not evaluate configurations against rules.
> - C: GuardDuty detects threats, not configuration compliance.
> - D: Artifact provides AWS compliance reports.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q10
A company wants to automatically discover and classify personally identifiable information (PII) stored in its Amazon S3 buckets. Which service should it use?

- A. Amazon Detective
- B. Amazon Inspector
- C. Amazon GuardDuty
- D. Amazon Macie

> [!success]- Answer
> **D.** Macie uses machine learning and pattern matching to find sensitive data such as PII in S3.
> - A: Detective investigates the root cause of findings.
> - B: Inspector scans workloads for software vulnerabilities.
> - C: GuardDuty detects threats from log activity.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q11
A company wants to encrypt data in transit between users' browsers and its Application Load Balancer, and have certificates renew automatically. Which service should it use?

- A. AWS Key Management Service (AWS KMS)
- B. AWS Certificate Manager (ACM)
- C. AWS CloudHSM
- D. AWS Secrets Manager

> [!success]- Answer
> **B.** ACM provisions and automatically renews SSL/TLS certificates used for HTTPS (encryption in transit) on integrated services such as Elastic Load Balancing.
> - A: KMS manages encryption keys, mainly for data at rest.
> - C: CloudHSM is a dedicated HSM for key storage, not certificate management.
> - D: Secrets Manager stores and rotates credentials.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q12
A company's EC2 instance begins communicating with an IP address known for cryptocurrency mining. Which service is designed to detect this activity?

- A. Amazon GuardDuty
- B. AWS Config
- C. Amazon Macie
- D. AWS Trusted Advisor

> [!success]- Answer
> **A.** GuardDuty provides intelligent threat detection by analyzing CloudTrail events, VPC Flow Logs, and DNS logs with threat intelligence.
> - B: Config tracks configurations, not traffic threats.
> - C: Macie finds sensitive data in S3.
> - D: Trusted Advisor checks configuration best practices, not live threats.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q13
A security team uses several AWS accounts and wants a single place to view and prioritize findings from Amazon GuardDuty, Amazon Inspector, and Amazon Macie, and to check accounts against security best practice standards. Which service should it use?

- A. Amazon Detective
- B. AWS Audit Manager
- C. AWS Security Hub
- D. Amazon CloudWatch

> [!success]- Answer
> **C.** Security Hub aggregates findings across accounts and runs automated checks against standards such as AWS Foundational Security Best Practices.
> - A: Detective investigates root causes; it does not aggregate all findings into a posture dashboard.
> - B: Audit Manager collects audit evidence against compliance frameworks.
> - D: CloudWatch monitors metrics and logs.
>
> Review: [[2.2 Security, Governance, and Compliance Concepts]]

### Q14
An application running on an Amazon EC2 instance needs to read objects from an Amazon S3 bucket. What is the most secure way to grant this access?

- A. Attach an IAM role with the required S3 permissions to the instance
- B. Store an IAM user's access keys in a configuration file on the instance
- C. Use the root user's access keys in the application
- D. Make the S3 bucket public

> [!success]- Answer
> **A.** An IAM role gives the instance temporary credentials that rotate automatically, with least-privilege permissions.
> - B: Long-term keys on an instance can leak and must be rotated manually.
> - C: Root access keys should never be created or used.
> - D: Public access exposes the data to everyone.
>
> Review: [[2.3 Access Management and IAM]]

### Q15
Which tasks can be performed only by the AWS account root user? (Select TWO.)

- A. Creating an IAM group for administrators
- B. Closing the AWS account
- C. Launching an Amazon EC2 instance
- D. Enabling MFA Delete on an Amazon S3 bucket
- E. Creating a customer managed IAM policy

> [!success]- Answer
> **B and D.** Closing a standalone account and configuring an S3 bucket for MFA Delete both require root user credentials.
> - A: Any IAM identity with IAM permissions can create groups.
> - C: Any identity with EC2 permissions can launch instances.
> - E: Any identity with IAM permissions can create policies.
>
> Review: [[2.3 Access Management and IAM]]

### Q16
A company has just created a new AWS account. Which actions follow AWS best practices for protecting the root user? (Select TWO.)

- A. Enable multi-factor authentication (MFA) on the root user
- B. Create access keys for the root user for use in automation scripts
- C. Use the root user for daily administrative tasks
- D. Create an administrative identity for everyday work and avoid using the root user
- E. Share the root user password with the operations team

> [!success]- Answer
> **A and D.** Secure root with MFA and use a separate administrative identity for daily work.
> - B: Root access keys should not exist.
> - C: Root should be used only for root-only tasks.
> - E: Root credentials must be tightly restricted, not shared.
>
> Review: [[2.3 Access Management and IAM]]

### Q17
A company has 40 developers who all need the same set of permissions. The security team wants to manage these permissions in one place and follow the principle of least privilege. What should the team do?

- A. Attach an inline policy to each developer's IAM user
- B. Have the developers share one IAM user
- C. Attach the AdministratorAccess AWS managed policy to each developer
- D. Create an IAM group, attach a customer managed policy with only the needed permissions, and add the developers to the group

> [!success]- Answer
> **D.** Groups apply permissions to many users at once, and a customer managed policy can be scoped precisely and reused.
> - A: Forty inline policies are hard to manage and not reusable.
> - B: Shared credentials remove accountability and violate best practice.
> - C: Administrator access violates least privilege.
>
> Review: [[2.3 Access Management and IAM]]

### Q18
A company wants its employees to sign in once with their existing corporate credentials and access several AWS accounts and business applications from a single portal. Which service should it use?

- A. Amazon Cognito
- B. AWS Secrets Manager
- C. AWS IAM Identity Center (AWS Single Sign-On)
- D. AWS Resource Access Manager (AWS RAM)

> [!success]- Answer
> **C.** IAM Identity Center manages workforce sign-in and single sign-on across AWS accounts and applications, and can federate with a corporate identity provider.
> - A: Cognito is for end users of web and mobile applications.
> - B: Secrets Manager stores credentials; it does not provide sign-in.
> - D: AWS RAM shares resources between accounts, not user sign-in.
>
> Review: [[2.3 Access Management and IAM]]

### Q19
An application connects to an Amazon RDS database. The company wants to remove the hard-coded database password from the code and have the password changed automatically every 30 days. Which service meets these requirements with the least effort?

- A. AWS Systems Manager Parameter Store
- B. AWS Key Management Service (AWS KMS)
- C. AWS Secrets Manager
- D. AWS Certificate Manager (ACM)

> [!success]- Answer
> **C.** Secrets Manager stores secrets and has built-in automatic rotation for RDS credentials.
> - A: Parameter Store can store the password but has no built-in rotation.
> - B: KMS manages encryption keys, not database passwords.
> - D: ACM manages SSL/TLS certificates.
>
> Review: [[2.3 Access Management and IAM]]

### Q20
A mobile game needs to let millions of players sign up and sign in with their Google or Apple accounts. Which service should the developers use?

- A. AWS IAM Identity Center
- B. AWS Directory Service
- C. IAM users with password policies
- D. Amazon Cognito

> [!success]- Answer
> **D.** Cognito provides sign-up, sign-in, and federation with social identity providers for web and mobile app users.
> - A: Identity Center is for workforce users, not app customers.
> - B: Directory Service provides Microsoft Active Directory.
> - C: IAM users are for access to AWS itself, not app end users, and do not scale to millions.
>
> Review: [[2.3 Access Management and IAM]]

### Q21
Which statements correctly describe security groups and network ACLs? (Select TWO.)

- A. Security groups are stateful and operate at the instance level
- B. Network ACLs support only allow rules
- C. Network ACLs are stateless and operate at the subnet level
- D. Security groups evaluate rules in number order and stop at the first match
- E. Security groups support explicit deny rules

> [!success]- Answer
> **A and C.** Security groups are stateful instance-level firewalls; network ACLs are stateless subnet-level firewalls.
> - B: Network ACLs support allow and deny rules.
> - D: Numbered first-match evaluation describes network ACLs; security groups evaluate all rules together.
> - E: Security groups support allow rules only.
>
> Review: [[2.4 Security Components and Resources]]

### Q22
A company's public website on Amazon CloudFront is receiving requests that attempt SQL injection. Which service should the company use to block these requests?

- A. AWS Shield Standard
- B. Network ACLs
- C. AWS WAF
- D. Amazon Inspector

> [!success]- Answer
> **C.** AWS WAF inspects HTTP(S) requests and blocks common web exploits such as SQL injection and cross-site scripting.
> - A: Shield Standard protects against network and transport layer DDoS, not SQL injection.
> - B: NACLs filter by IP address and port, not request content, and do not apply to CloudFront.
> - D: Inspector scans workloads for vulnerabilities; it does not block requests.
>
> Review: [[2.4 Security Components and Resources]]

### Q23
A company that relies on a critical public application wants 24/7 access to DDoS response experts and protection against scaling charges caused by DDoS attacks. Which option should it choose?

- A. AWS Shield Standard
- B. AWS Shield Advanced
- C. AWS Firewall Manager
- D. Amazon GuardDuty

> [!success]- Answer
> **B.** Shield Advanced adds the Shield Response Team (with Business or Enterprise Support) and DDoS cost protection.
> - A: Shield Standard is free and automatic but has no response team or cost protection.
> - C: Firewall Manager centrally manages policies; it is not the DDoS protection itself.
> - D: GuardDuty detects threats; it does not mitigate DDoS.
>
> Review: [[2.4 Security Components and Resources]]

### Q24
A company uses AWS Organizations with 60 accounts. The security team wants AWS WAF rules and security group policies applied consistently to every existing and new account. Which service should it use?

- A. AWS Firewall Manager
- B. AWS Network Firewall
- C. AWS Config
- D. AWS Shield Standard

> [!success]- Answer
> **A.** Firewall Manager centrally configures and enforces WAF rules, Shield Advanced protections, and security group policies across accounts in an organization.
> - B: Network Firewall filters traffic for a VPC; it does not manage rules across accounts.
> - C: Config evaluates configurations but does not deploy firewall rules.
> - D: Shield Standard is automatic DDoS protection with no rules to manage.
>
> Review: [[2.4 Security Components and Resources]]

### Q25
A company on the Basic Support plan wants an AWS tool that checks whether MFA is enabled on the root user and whether security groups allow unrestricted access to specific ports. Which service provides these checks?

- A. Amazon Inspector
- B. AWS Knowledge Center
- C. AWS Artifact
- D. AWS Trusted Advisor

> [!success]- Answer
> **D.** Trusted Advisor core security checks (available on every plan) include MFA on root account and security groups with specific ports unrestricted.
> - A: Inspector scans workloads for software vulnerabilities and network reachability, not root MFA.
> - B: Knowledge Center is a set of help articles, not an account checker.
> - C: Artifact provides compliance reports.
>
> Review: [[2.4 Security Components and Resources]]
