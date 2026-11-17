---
tags:
  - clf-c02
  - services
  - services/customer-engagement
category: "Customer Engagement"
status: not-started
---
# Services: Customer Engagement

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Support plans, AWS Partners, Professional Services, re:Post, and the other help resources are taught in [[4.3 Technical Resources and Support Options]] and [[3.8 Other In-Scope Service Categories]]. One-page summary: [[Support Plans]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#AWS Activate for Startups]] | Credits, training, and support for startups | "Startup", "early-stage company", "AWS credits", "founders" |
| [[#AWS IQ]] | Marketplace to hire AWS Certified freelance experts | "Hire a certified expert", "freelancer", "on-demand project help" |
| [[#AWS Managed Services (AMS)]] | AWS operates your infrastructure for you | "Ongoing operations", "outsource day-to-day management", "patching, monitoring, incident response done by AWS" |
| [[#AWS Support]] | Tiered support plans for technical and account help | "Response time", "TAM", "24/7 phone", "Trusted Advisor checks" |

> [!tip] Who helps you?
> Startup money and resources: **Activate**. A short project from an individual certified expert: **IQ**. AWS runs operations long term: **AMS**. Answers to cases and guidance: **AWS Support**. A large engagement with AWS consultants: **AWS Professional Services**. Architecture guidance: **AWS Solutions Architects**. A third-party firm: **AWS Partner Network** (see [[4.3 Technical Resources and Support Options]]).

## AWS Activate for Startups

> [!summary] Provides resources to help startups build and grow on AWS.

- **What it does:** A program for startups that offers AWS promotional credits, technical support, training, and other resources. Self-funded startups and startups backed by an Activate Provider (accelerators, incubators, venture capital firms) can apply.
- **Choose it when:** The scenario describes a startup or new company looking for free credits, startup guidance, or resources to launch on AWS.
- **Key facts:**
  - Benefits include ==AWS credits==, technical resources, training, and access to startup-focused offers.
  - Aimed at startups specifically, not at established enterprises.
  - Free to apply; eligibility depends on company stage and funding.
- **Don't confuse with:** The AWS Free Tier (free usage limits for every new account, not a startup program) and the AWS Partner Network (for companies that build or sell solutions on AWS).
- **Docs:** [AWS Activate](https://aws.amazon.com/activate/)

## AWS IQ

> [!summary] Connects users to AWS Certified experts for help with AWS projects.

- **What it does:** A marketplace where customers post a project request and receive proposals from AWS Certified freelancers and consulting firms. You pick an expert, agree on terms, and pay through your AWS bill. Experts can be granted controlled access to your account.
- **Choose it when:** A company needs hands-on help from a certified third-party expert for a defined, often short project and wants to pay through AWS.
- **Key facts:**
  - Experts are ==AWS Certified== freelancers or consulting firms, not AWS employees.
  - Payment is milestone- or hourly-based and billed to the AWS account.
  - Customer controls what access the expert gets to the account.
- **Don't confuse with:** [[#AWS Managed Services (AMS)]] (AWS itself runs operations ongoing), AWS Professional Services (AWS's own consultants for large engagements), and [[#AWS Support]] (case-based help, not someone doing the work).
- **Docs:** [Services in Full Shutdown, AWS General Reference](https://docs.aws.amazon.com/general/latest/gr/full_shutdown_services.html)

Current status: AWS lists AWS IQ as fully shut down, with an end-of-support date of May 20, 2026 (AWS General Reference, "Services in Full Shutdown"). The exam guide still lists it, so know what it was.

## AWS Managed Services (AMS)

> [!summary] Provides ongoing management for a user's AWS infrastructure.

- **What it does:** AWS staff operate your AWS environment for you using AWS best practices: monitoring, incident management, patching, backup, security, change management, and cost optimization. It lets an enterprise move to AWS without building a full cloud operations team.
- **Choose it when:** A company lacks in-house cloud operations skills and wants AWS to handle day-to-day infrastructure operations on an ongoing basis.
- **Key facts:**
  - ==Ongoing operational management by AWS==, not a one-time project.
  - Covers patching, monitoring, incident response, backups, and security controls.
  - Aimed at enterprises; it adds cost on top of the AWS services used.
  - Has two operating models: AMS Accelerate (works in your existing accounts) and AMS Advanced (AMS-managed landing zone).
- **Don't confuse with:** [[#AWS Support]] (answers questions and cases but does not operate your environment), AWS Professional Services (project-based consulting), and [[Services - Management and Governance#AWS Systems Manager|AWS Systems Manager]] (a tool you use yourself to manage resources).
- **Docs:** [What is AWS Managed Services?](https://docs.aws.amazon.com/managedservices/latest/userguide/what-is-ams.html)

Current status: AMS Advanced stopped accepting new customers on June 30, 2026 and reaches end of support on June 30, 2027; AWS points customers to AMS Accelerate and other options.

## AWS Support

> [!summary] Tiered support plans that give access to AWS experts, tools, and guidance. (No one-line summary in the reference guide; the plan comparison table is in [[Support Plans]].)

- **What it does:** Every account gets Basic Support (account and billing help, documentation, AWS re:Post, AWS Health Dashboard, core Trusted Advisor checks). Paid plans add technical support cases, faster response times, more Trusted Advisor checks, and, at the top, a Technical Account Manager (TAM).
- **Choose it when:** The question is about getting technical help from AWS, response-time commitments, Trusted Advisor check coverage, or access to a TAM or Concierge team.
- **Key facts:**
  - Exam plans: ==Basic, Developer, Business, Enterprise On-Ramp, Enterprise==.
  - Fastest response times (reference guide): Developer general guidance 24 business hours, system impaired 12 business hours; Business production system down 1 hour; Enterprise business-critical system down ==15 minutes== (Enterprise On-Ramp is 30 minutes).
  - Full set of Trusted Advisor checks starts at Business; Basic and Developer get core checks only.
  - Designated TAM: Enterprise. Pool of TAMs: Enterprise On-Ramp. Concierge Support team: Enterprise On-Ramp and Enterprise.
  - Account and billing questions are free on every plan; AWS Support Center in the console is where you open cases.
- **Don't confuse with:** [[#AWS Managed Services (AMS)]] (AWS runs your operations) and [[Services - Management and Governance#AWS Trusted Advisor|AWS Trusted Advisor]] (automated best-practice checks, whose coverage depends on the support plan). Abuse reports (spam, DDoS from AWS IPs) go to the AWS Trust and Safety team, not Support.
- **Docs:** [AWS Support plans](https://docs.aws.amazon.com/awssupport/latest/user/aws-support-plans.html)

Current status: AWS now sells Basic, Business Support+, Enterprise, and Unified Operations plans. Developer, Business, and Enterprise On-Ramp are discontinued on January 1, 2027 (AWS Support User Guide). The exam still uses the five-plan model above.

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
