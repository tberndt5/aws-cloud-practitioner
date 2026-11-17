---
tags:
  - clf-c02
  - services
  - services/security-identity-and-compliance
category: "Security, Identity, and Compliance"
status: not-started
---
# Services: Security, Identity, and Compliance

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Domain 2 is 30% of the exam, and most of it is about the services below. Concepts are taught in the task notes: who secures what in [[2.1 Shared Responsibility Model]], compliance, encryption, and logging in [[2.2 Security, Governance, and Compliance Concepts]], identities, root user, MFA, and least privilege in [[2.3 Access Management and IAM]], and security groups, network ACLs, and security information sources in [[2.4 Security Components and Resources]].

| Service | What it is | Cue in a question |
|---|---|---|
| [[#AWS Artifact]] | Portal for AWS compliance reports and agreements | "download SOC or PCI report", "sign a BAA" |
| [[#AWS Audit Manager]] | Continuous evidence collection for your audits | "prepare for an audit", "collect evidence automatically" |
| [[#AWS Certificate Manager (ACM)]] | SSL/TLS certificates, free public certs, auto-renewal | "HTTPS certificate", "renew certificates automatically" |
| [[#AWS CloudHSM]] | Dedicated single-tenant hardware security modules | "dedicated HSM", "full control of keys", "single-tenant" |
| [[#Amazon Cognito]] | Sign-up and sign-in for app end users | "users of my web or mobile app", "social login" |
| [[#Amazon Detective]] | Investigate root cause of security findings | "investigate", "root cause", "visualize what happened" |
| [[#AWS Directory Service]] | Managed Microsoft Active Directory | "Active Directory", "domain join", "LDAP" |
| [[#AWS Firewall Manager]] | Central firewall rules across accounts | "apply WAF rules across all accounts in the organization" |
| [[#Amazon GuardDuty]] | Intelligent threat detection from logs | "threat detection", "unusual API calls", "compromised instance" |
| [[#AWS Identity and Access Management (IAM)]] | Users, groups, roles, and permission policies | "permissions", "least privilege", "role for EC2" |
| [[#AWS IAM Identity Center (AWS Single Sign-On)]] | Workforce single sign-on across accounts and apps | "employees sign in once to many accounts" |
| [[#Amazon Inspector]] | Automated vulnerability scanning of workloads | "software vulnerabilities", "CVEs", "unintended network exposure" |
| [[#AWS Key Management Service (AWS KMS)]] | Managed encryption keys | "create and control encryption keys", "encryption at rest" |
| [[#Amazon Macie]] | Find sensitive data (PII) in S3 | "PII", "sensitive data in S3 buckets" |
| [[#AWS Network Firewall]] | Managed stateful firewall and IPS for a VPC | "intrusion prevention for VPC", "filter traffic at VPC perimeter" |
| [[#AWS Resource Access Manager (AWS RAM)]] | Share resources across accounts | "share subnets or Transit Gateway with other accounts" |
| [[#AWS Secrets Manager]] | Store and automatically rotate secrets | "rotate database credentials", "no hardcoded passwords" |
| [[#AWS Security Hub]] | Central security findings and posture checks | "single view of security findings", "check against CIS benchmark" |
| [[#AWS Shield]] | DDoS protection | "DDoS" |
| [[#AWS WAF]] | Web application firewall for HTTP(S) | "SQL injection", "cross-site scripting", "block IPs or countries" |

> [!tip] Memory hooks for the detection family
> **GuardDuty** = guard: watches logs for threats. **Inspector** = inspects your software for vulnerabilities. **Macie** = finds sensitive data in S3. **Detective** = investigates after a finding. **Security Hub** = the hub that collects everyone's findings and scores you against standards.

## AWS Artifact

> [!summary] Download security and compliance documents.

- **What it does:** A free, self-service portal in the console for on-demand access to AWS's own compliance reports (from third-party auditors) and to review and accept agreements with AWS.
- **Choose it when:** The question asks where to get AWS's SOC reports, PCI DSS attestation, ISO certifications, or other evidence that AWS itself is compliant, or how to accept an agreement such as a Business Associate Addendum (BAA) for HIPAA. The exam guide names Artifact as the place to find AWS compliance information.
- **Key facts:**
  - **Artifact Reports**: AWS security and compliance reports, such as SOC 1/2/3, PCI, and ISO.
  - **Artifact Agreements**: review, accept, and manage agreements such as the BAA, for an account or a whole organization.
  - Free.
  - Proves the AWS side of shared responsibility ("security of the cloud"); your own workload's compliance is still your job.
- **Don't confuse with:** [[#AWS Audit Manager]] gathers evidence about **your** use of AWS for **your** audits; Artifact provides **AWS's** reports. The AWS Compliance Programs website explains which programs AWS meets; Artifact is where you download the documents.
- **Docs:** [What is AWS Artifact?](https://docs.aws.amazon.com/artifact/latest/ug/what-is-aws-artifact.html)

## AWS Audit Manager

> [!summary] Continually audit AWS usage to manage risk and to comply with regulations and industry standards.

- **What it does:** Automatically and continuously collects evidence from your AWS accounts (for example, from AWS Config, CloudTrail, and Security Hub) and maps it to controls in prebuilt or custom frameworks, producing audit-ready reports.
- **Choose it when:** A company wants to simplify preparing for an internal or external audit, continuously assess compliance with a framework such as PCI DSS, HIPAA, or GDPR, or replace manual evidence gathering. The exam guide lists it under auditing.
- **Key facts:**
  - Prebuilt frameworks for common standards and regulations; you can build custom ones.
  - Evidence is collected automatically and organized by control.
  - Produces assessment reports for auditors.
  - Does not itself certify that you are compliant; it organizes evidence.
- **Don't confuse with:** [[#AWS Artifact]] (download AWS's own compliance reports). [[Services - Management and Governance#AWS Config|AWS Config]] (evaluates resource configurations against rules; Audit Manager can use its results as evidence). [[#AWS Security Hub]] (security posture checks and findings).
- **Docs:** [What is AWS Audit Manager?](https://docs.aws.amazon.com/audit-manager/latest/userguide/what-is.html)

## AWS Certificate Manager (ACM)

> [!summary] Creates, stores, and renews public and private SSL/TLS certificates.

- **What it does:** Provisions and manages SSL/TLS certificates that enable HTTPS (encryption in transit) and handles their renewal automatically.
- **Choose it when:** The question asks how to get, deploy, or automatically renew SSL/TLS certificates for a website, load balancer, CloudFront distribution, or API.
- **Key facts:**
  - Public certificates for use with ACM-integrated services are ==free==.
  - Integrates with Elastic Load Balancing, Amazon CloudFront, and Amazon API Gateway.
  - Automatic renewal of ACM-issued certificates.
  - Supports encryption **in transit**; KMS is the at-rest counterpart.
- **Don't confuse with:** [[#AWS Key Management Service (AWS KMS)]] manages encryption keys for data at rest. [[#AWS Secrets Manager]] stores passwords and API keys. [[#AWS CloudHSM]] is hardware for keys you control.
- **Docs:** [What is AWS Certificate Manager?](https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html)
- Current status: since June 2025, ACM can also issue exportable public certificates (for a fee) that you can install on EC2, containers, or on-premises servers ([AWS announcement](https://aws.amazon.com/about-aws/whats-new/2025/06/aws-certificate-manager-public-certificates-use-anywhere/)). For the exam, think "free certificates for integrated services such as ELB, CloudFront, and API Gateway".

## AWS CloudHSM

> [!summary] Provides a compute device that processes cryptographic operations and storage.

- **What it does:** Gives you dedicated, single-tenant hardware security modules (HSMs) in the AWS Cloud. You alone manage the keys and users on the HSM; AWS manages the hardware but has no access to your keys.
- **Choose it when:** The scenario requires a dedicated or single-tenant HSM, exclusive customer control of keys, or strict regulatory requirements for validated hardware that only the customer controls.
- **Key facts:**
  - Single-tenant, dedicated hardware in your VPC; FIPS-validated HSMs.
  - The customer manages keys and HSM users; if you lose the credentials, AWS cannot recover your keys.
  - More operational effort than KMS.
  - KMS can use a CloudHSM cluster as a custom key store.
- **Don't confuse with:** [[#AWS Key Management Service (AWS KMS)]] is the default answer for encryption keys: fully managed, multi-tenant, integrated with most AWS services. Choose CloudHSM only when "dedicated", "single-tenant", or "customer-exclusive control of the HSM" appears. [[#AWS Certificate Manager (ACM)]] handles certificates, not HSMs.
- **Docs:** [What is AWS CloudHSM?](https://docs.aws.amazon.com/cloudhsm/latest/userguide/introduction.html)

## Amazon Cognito

> [!summary] Identity platform for web and mobile applications, including federation for third parties.

- **What it does:** Adds sign-up, sign-in, and access control for the **end users (customers)** of your web and mobile apps. Users can sign in with a username and password or through social and enterprise identity providers such as Google, Facebook, Apple, or SAML.
- **Choose it when:** The scenario involves millions of app users or customers signing in to an application, social login, or giving app users temporary access to AWS resources such as S3.
- **Key facts:**
  - **User pools**: a user directory that handles sign-up and sign-in.
  - **Identity pools**: exchange a signed-in identity for temporary AWS credentials.
  - Supports MFA and federation with third-party identity providers.
  - Scales to millions of users.
- **Don't confuse with:** [[#AWS Identity and Access Management (IAM)]] controls access to AWS for your own people and services, not app customers. [[#AWS IAM Identity Center (AWS Single Sign-On)]] is single sign-on for your **workforce** (employees). [[#AWS Directory Service]] runs Microsoft Active Directory.
- **Docs:** [What is Amazon Cognito?](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)

## Amazon Detective

> [!summary] Analyze, investigate, and identify the root cause of security findings or suspicious activities.

- **What it does:** Automatically collects log data (such as CloudTrail logs, VPC Flow Logs, and GuardDuty findings) and builds linked, visual graphs of activity, so security analysts can investigate what happened, how far it spread, and why.
- **Choose it when:** The question uses words like "investigate", "root cause", or "analyze the scope of a security finding" after something has already been detected.
- **Key facts:**
  - Works after detection: GuardDuty finds, Detective investigates.
  - Uses machine learning, statistical analysis, and graph theory.
  - Needs no agents and no log pipeline setup.
- **Don't confuse with:** [[#Amazon GuardDuty]] **detects** threats; Detective **investigates** them. [[#AWS Security Hub]] **aggregates** findings and checks posture. [[Services - Management and Governance#AWS CloudTrail|CloudTrail]] supplies raw API logs but no analysis.
- **Docs:** [What is Amazon Detective?](https://docs.aws.amazon.com/detective/latest/userguide/what-is-detective.html)

## AWS Directory Service

> [!summary] Provides multiple ways to set up and run Microsoft Active Directory with AWS services.

- **What it does:** Lets you use Microsoft Active Directory (AD) in AWS, either as a fully managed AD in the cloud or by connecting AWS services to your existing on-premises AD.
- **Choose it when:** The scenario mentions Microsoft Active Directory, domain-joining EC2 Windows instances, LDAP, Group Policy, or AD-aware workloads such as SQL Server or WorkSpaces.
- **Key facts:**
  - **AWS Managed Microsoft AD**: an actual Microsoft AD run by AWS; can have a trust with on-premises AD.
  - **AD Connector**: a proxy that redirects requests to your existing on-premises AD without storing directory data in the cloud.
  - **Simple AD**: a basic, low-cost AD-compatible directory.
  - Can be an identity source for IAM Identity Center.
- **Don't confuse with:** [[#AWS IAM Identity Center (AWS Single Sign-On)]] provides single sign-on to AWS accounts and apps (it can use AD as its identity source). [[#AWS Identity and Access Management (IAM)]] is AWS's native permission system. [[#Amazon Cognito]] is for app customers.
- **Docs:** [What is AWS Directory Service?](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/what_is.html)

## AWS Firewall Manager

> [!summary] Provides administration and maintenance tasks across multiple accounts and resources for a variety of protections.

- **What it does:** Centrally configures and enforces firewall and protection rules across all accounts in AWS Organizations, and applies them automatically to new accounts and resources.
- **Choose it when:** A company with many accounts wants to apply the same WAF rules, Shield Advanced protections, security group policies, or Network Firewall rules everywhere from one place.
- **Key facts:**
  - Requires AWS Organizations.
  - Manages AWS WAF, AWS Shield Advanced, VPC security groups, AWS Network Firewall, and Route 53 Resolver DNS Firewall, among others.
  - New resources that match a policy are protected automatically.
  - It manages other protections; it does not inspect traffic itself.
- **Don't confuse with:** [[#AWS WAF]] is the web firewall itself; Firewall Manager rolls out WAF rules across accounts. [[#AWS Network Firewall]] filters traffic for a VPC. [[#AWS Shield]] is the DDoS protection.
- **Docs:** [AWS Firewall Manager (Developer Guide)](https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html)

## Amazon GuardDuty

> [!summary] Intelligent threat detection that provides continuous monitoring.

- **What it does:** Continuously analyzes AWS data sources with machine learning, anomaly detection, and threat intelligence to find malicious or unauthorized activity, such as compromised credentials, crypto-mining instances, or calls from known malicious IP addresses.
- **Choose it when:** The question asks for continuous threat detection, finding unusual API activity or account compromise, or detecting malicious behavior without deploying agents.
- **Key facts:**
  - Core data sources: ==CloudTrail events, VPC Flow Logs, and DNS logs==; optional protection plans cover S3, EKS, RDS, Lambda, and malware scanning.
  - Enable with a few clicks; no agents or software required for the core sources.
  - Produces findings with severity levels; findings can go to Security Hub and EventBridge.
  - Can be managed across accounts in an organization.
- **Don't confuse with:** [[#Amazon Inspector]] scans for software vulnerabilities. [[#Amazon Macie]] finds sensitive data in S3. [[#Amazon Detective]] investigates findings. [[#AWS Security Hub]] aggregates findings. [[#AWS Shield]] protects against DDoS.
- **Docs:** [What is Amazon GuardDuty?](https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html)

## AWS Identity and Access Management (IAM)

> [!summary] Helps users securely control access to AWS resources.

- **What it does:** Controls **who** is authenticated (signed in) and **what** they are authorized to do in an AWS account, through users, groups, roles, and permission policies.
- **Choose it when:** The question involves granting or limiting permissions, giving an EC2 instance or Lambda function access to another service, cross-account access, MFA, or applying least privilege.
- **Key facts:**
  - **Users** (long-term credentials for a person or app), **groups** (collections of users; attach policies once), **roles** (temporary credentials assumed by services, users, or other accounts), **policies** (JSON documents that allow or deny actions).
  - AWS managed policies versus customer managed (custom) policies; follow the principle of least privilege.
  - IAM is global and free.
  - Protect the root user: enable MFA, do not create root access keys, use it only for root-only tasks.
  - Prefer roles over long-term access keys; IAM credential reports and access advisor support access reviews.
- **Don't confuse with:** [[#AWS IAM Identity Center (AWS Single Sign-On)]] (workforce single sign-on across many accounts). [[#Amazon Cognito]] (customer identities for apps). [[Services - Management and Governance#AWS Organizations|AWS Organizations]] SCPs (cap the permissions of whole accounts; they grant nothing). See [[2.3 Access Management and IAM]].
- **Docs:** [What is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)

## AWS IAM Identity Center (AWS Single Sign-On)

> [!summary] Manage sign-in security for workforce identities.

- **What it does:** Gives employees (the workforce) one sign-in to access multiple AWS accounts in AWS Organizations and business applications. Administrators assign permission sets centrally.
- **Choose it when:** The scenario needs single sign-on for staff across many AWS accounts, central management of workforce access, or federation with a corporate identity provider such as Microsoft Active Directory, Okta, or Microsoft Entra ID.
- **Key facts:**
  - Successor to AWS Single Sign-On (renamed in 2022); the exam uses both names.
  - Identity sources: its own built-in directory, Active Directory (through Directory Service), or an external SAML 2.0 identity provider.
  - **Permission sets** define access in each account; users get short-term credentials.
  - Recommended approach for human access to AWS instead of creating IAM users in each account.
- **Don't confuse with:** [[#AWS Identity and Access Management (IAM)]] manages permissions inside an account. [[#Amazon Cognito]] is for customers of your apps, not employees. [[#AWS Directory Service]] runs the AD that Identity Center can connect to.
- **Docs:** [What is IAM Identity Center?](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)

## Amazon Inspector

> [!summary] Continuously scans AWS workloads for software vulnerabilities and unintended network exposure.

- **What it does:** Automatically discovers workloads and continuously scans them for known software vulnerabilities (CVEs) and unintended network exposure, then gives each finding a risk score.
- **Choose it when:** The question asks how to find vulnerabilities or missing patches in EC2 instances, container images, or Lambda functions, or how to detect instances reachable from the internet unintentionally.
- **Key facts:**
  - Scans ==EC2 instances, container images in Amazon ECR, and Lambda functions==.
  - Continuous and automatic; rescans when new CVEs are published or software changes.
  - EC2 scanning uses the Systems Manager agent (or agentless scanning).
  - Findings flow to Security Hub and EventBridge.
- **Don't confuse with:** [[#Amazon GuardDuty]] detects active threats from logs. [[Services - Management and Governance#AWS Trusted Advisor|Trusted Advisor]] checks account-level best practices, not software CVEs. [[#Amazon Macie]] finds sensitive data. [[Services - Management and Governance#AWS Systems Manager|Systems Manager Patch Manager]] applies patches; Inspector finds what needs patching.
- **Docs:** [What is Amazon Inspector?](https://docs.aws.amazon.com/inspector/latest/user/what-is-inspector.html)

## AWS Key Management Service (AWS KMS)

> [!summary] Create and control cryptographic keys that protect user data.

- **What it does:** A managed service for creating, storing, rotating, and controlling access to the encryption keys used to encrypt data, mainly **at rest**. Keys are protected by hardware security modules and never leave KMS unencrypted.
- **Choose it when:** The question asks how to encrypt data in S3, EBS, RDS, or other services, how to manage or rotate encryption keys, or how to control and audit who can use a key.
- **Key facts:**
  - Integrated with most AWS services that store data.
  - **AWS managed keys** (created by a service for you) versus **customer managed keys** (you create and control policies and rotation).
  - Key use is logged in CloudTrail; access is controlled with key policies and IAM.
  - Multi-tenant and fully managed, with less overhead than CloudHSM.
- **Don't confuse with:** [[#AWS CloudHSM]] (dedicated single-tenant HSM you manage). [[#AWS Certificate Manager (ACM)]] (TLS certificates for encryption in transit). [[#AWS Secrets Manager]] (stores secrets such as passwords; it uses KMS to encrypt them).
- **Docs:** [What is AWS KMS?](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)

## Amazon Macie

> [!summary] Discovers sensitive data, PII, and security risks, then provides automated protection against those risks.

- **What it does:** Uses machine learning and pattern matching to discover and classify sensitive data, such as personally identifiable information (PII), financial data, or credentials, stored in Amazon S3, and to flag S3 buckets with security risks such as public access or no encryption.
- **Choose it when:** The scenario mentions PII, sensitive data discovery, data privacy compliance (for example GDPR), or finding which S3 buckets contain sensitive data.
- **Key facts:**
  - Focused on ==Amazon S3==.
  - Produces sensitive-data findings and policy findings (bucket-level risks).
  - Findings can go to Security Hub and EventBridge.
- **Don't confuse with:** [[#Amazon GuardDuty]] (threat detection from logs; it may flag suspicious S3 access but does not classify data). [[#Amazon Inspector]] (software vulnerabilities). [[#AWS Key Management Service (AWS KMS)]] encrypts data; Macie finds and classifies it.
- **Docs:** [What is Amazon Macie?](https://docs.aws.amazon.com/macie/latest/user/what-is-macie.html)

## AWS Network Firewall

> [!summary] Provides intrusion detection and prevention for a VPC.

- **What it does:** A managed, stateful network firewall and intrusion detection and prevention system (IDS/IPS) deployed at the perimeter of a VPC. It filters traffic going in and out of the VPC, including to the internet, other VPCs, and on-premises networks.
- **Choose it when:** The question asks for network-level traffic filtering, intrusion prevention, or domain-based outbound filtering for an entire VPC, beyond what security groups and network ACLs offer.
- **Key facts:**
  - Stateful and stateless rules; supports Suricata-compatible IPS rules and domain allow and deny lists.
  - Scales automatically; no firewall appliances to manage.
  - Can be centrally managed across accounts with Firewall Manager.
- **Don't confuse with:** [[#AWS WAF]] protects web applications at layer 7 (HTTP) on CloudFront, ALB, and API Gateway; Network Firewall protects the VPC at the network level. Security groups (instance level, stateful) and network ACLs (subnet level, stateless) are basic built-in VPC controls. [[#AWS Firewall Manager]] administers rules but does not filter traffic.
- **Docs:** [What is AWS Network Firewall?](https://docs.aws.amazon.com/network-firewall/latest/developerguide/what-is-aws-network-firewall.html)

## AWS Resource Access Manager (AWS RAM)

> [!summary] Securely share resources across AWS accounts.

- **What it does:** Lets you create a resource once and share it with other AWS accounts, OUs, or your entire organization, so you do not duplicate resources in every account.
- **Choose it when:** The scenario asks how to share resources such as VPC subnets, Transit Gateways, Route 53 Resolver rules, or License Manager configurations with other accounts.
- **Key facts:**
  - Shares within AWS Organizations or with specific accounts.
  - Reduces cost and operational overhead from duplicate resources.
  - No extra charge.
- **Don't confuse with:** [[Services - Management and Governance#AWS Organizations|AWS Organizations]] groups and governs accounts; RAM shares specific resources between them. Cross-account IAM roles let a user in one account act inside another; RAM makes a resource directly usable by other accounts.
- **Docs:** [What is AWS RAM?](https://docs.aws.amazon.com/ram/latest/userguide/what-is.html)

## AWS Secrets Manager

> [!summary] Manage and rotate credentials to improve security.

- **What it does:** Stores secrets such as database credentials, API keys, and OAuth tokens, encrypts them with KMS, and lets applications retrieve them at runtime instead of hardcoding them. It can rotate secrets automatically on a schedule.
- **Choose it when:** The question asks how to avoid hardcoded credentials or how to rotate database passwords automatically. The exam guide names Secrets Manager for credential storage.
- **Key facts:**
  - ==Automatic rotation==, with built-in support for Amazon RDS, Aurora, Redshift, and DocumentDB credentials.
  - Encrypted with KMS; access controlled by IAM; access logged in CloudTrail.
  - Paid per secret per month plus API calls.
- **Don't confuse with:** [[Services - Management and Governance#AWS Systems Manager|Systems Manager Parameter Store]] stores configuration values and secrets (free standard tier) but has no built-in automatic rotation. [[#AWS Key Management Service (AWS KMS)]] stores encryption keys, not passwords. [[#AWS Certificate Manager (ACM)]] stores TLS certificates.
- **Docs:** [What is AWS Secrets Manager?](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html)

## AWS Security Hub

> [!summary] Collects security data across accounts and identifies priority security issues.

- **What it does:** Gives a single, comprehensive view of your security state. It aggregates findings from GuardDuty, Inspector, Macie, and other AWS and partner tools across accounts, and runs automated checks against security standards to produce a security score.
- **Choose it when:** The question asks for a central dashboard of security findings across accounts, automated checks against best practices or a benchmark, or prioritizing security issues. The exam guide names it as a way customers secure resources.
- **Key facts:**
  - Standards include the AWS Foundational Security Best Practices, CIS AWS Foundations Benchmark, PCI DSS, and NIST.
  - Uses AWS Config rules for most of its checks, so Config must be enabled.
  - Findings use a common format; automated responses through EventBridge.
  - Multi-account through AWS Organizations; 30-day free trial.
- **Don't confuse with:** [[#Amazon GuardDuty]], [[#Amazon Inspector]], and [[#Amazon Macie]] each **produce** findings; Security Hub **collects and prioritizes** them. [[#Amazon Detective]] investigates individual findings. [[Services - Management and Governance#AWS Trusted Advisor|Trusted Advisor]] gives general best-practice checks, not aggregated security findings.
- **Docs:** [Introduction to AWS Security Hub CSPM](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html)
- Current status: in December 2025 AWS launched a new, unified AWS Security Hub that correlates findings into prioritized risks; the original service described here was renamed AWS Security Hub CSPM (cloud security posture management) and remains available ([AWS announcement](https://aws.amazon.com/about-aws/whats-new/2025/12/security-hub-near-real-time-risk-analytics/)). The exam uses "AWS Security Hub".

## AWS Shield

> [!summary] Provides protection against DDoS attacks for AWS resources.

- **What it does:** Protects applications running on AWS against distributed denial of service (DDoS) attacks, which try to overwhelm a resource with traffic.
- **Choose it when:** The question mentions DDoS. Choose **Standard** for basic, automatic, free protection; choose **Advanced** for larger or targeted attacks, expert help, and cost protection.
- **Key facts:**
  - **Shield Standard**: ==automatic and free== for all customers; protects against common network and transport layer (layer 3 and 4) attacks.
  - **Shield Advanced**: paid (US$3,000 per month with a 1-year commitment); enhanced protection for EC2, ELB, CloudFront, Global Accelerator, and Route 53; 24/7 access to the Shield Response Team (SRT); cost protection against scaling charges caused by an attack; includes AWS WAF at no extra charge for protected resources.
  - Shield Advanced requires Business or Enterprise Support for SRT access.
  - Using CloudFront and Route 53 adds edge-based DDoS resilience.
- **Don't confuse with:** [[#AWS WAF]] filters specific malicious web requests (SQL injection, XSS, bad IPs) at layer 7; Shield absorbs volumetric DDoS. [[#AWS Firewall Manager]] deploys Shield Advanced and WAF policies across accounts. [[#Amazon GuardDuty]] detects threats; it does not mitigate DDoS.
- **Docs:** [AWS Shield (Developer Guide)](https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html)

## AWS WAF

> [!summary] Monitor HTTP(S) requests and control access to web application resources.

- **What it does:** A web application firewall. You create rules (web ACLs) that allow, block, or count HTTP and HTTPS requests based on conditions such as IP address, country, headers, request body, or patterns typical of attacks.
- **Choose it when:** The question mentions SQL injection, cross-site scripting (XSS), blocking specific IP addresses or countries, rate limiting, or protecting a web application at the application layer. The exam guide names WAF as a security feature alongside security groups and network ACLs.
- **Key facts:**
  - Works at ==layer 7== (application layer, HTTP/HTTPS).
  - Attaches to Amazon CloudFront, Application Load Balancer, Amazon API Gateway, AWS AppSync, and Amazon Cognito user pools, among others; not directly to EC2 instances.
  - Managed rule groups from AWS and AWS Marketplace sellers give ready-made protections.
  - Rate-based rules help against HTTP floods.
- **Don't confuse with:** [[#AWS Shield]] (DDoS protection, mostly layers 3 and 4). [[#AWS Network Firewall]] (VPC-level network traffic filtering and IPS). Security groups filter by port and IP at the instance level and cannot inspect web request content. [[#AWS Firewall Manager]] manages WAF rules across accounts.
- **Docs:** [AWS WAF (Developer Guide)](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
