---
tags:
  - flashcards/domain-4
---
# Flashcards - Domain 4: Billing, Pricing, and Support

Review notes: [[4.1 AWS Pricing Models]] · [[4.2 Billing, Budget, and Cost Management]] · [[4.3 Technical Resources and Support Options]]

## 4.1 AWS pricing models

What are the AWS pricing principles?::Pay as you go; save when you commit; pay less by using more; volume discounts across an organization

Which pricing principle describes per-GB prices dropping as monthly usage grows?::Pay less by using more (tiered pricing)

Which EC2 option suits a new app with unknown, spiky usage that cannot be interrupted?::On-Demand Instances

Which EC2 option is cheapest for fault-tolerant batch work that can be interrupted?::Spot Instances (up to 90% off)

How much warning does AWS give before reclaiming a Spot Instance?::2 minutes

What terms and payment options do Reserved Instances and Savings Plans offer?::1 or 3 years; All Upfront, Partial Upfront, or No Upfront

Which RI term and payment option give the largest discount?::3-year, All Upfront

What are the maximum discounts for Standard and Convertible Reserved Instances?::Standard up to 72%; Convertible up to 66%

What is the key advantage of a Convertible RI over a Standard RI?::It can be exchanged for a different instance family, OS, or tenancy of equal or greater value

Which RI type can be sold on the Reserved Instance Marketplace?::Standard Reserved Instances only

What can you buy on the Reserved Instance Marketplace?::Third-party RIs, often with shorter remaining terms than 1 or 3 years

What do you commit to with a Savings Plan?::A consistent amount of compute spend in dollars per hour for 1 or 3 years

Which Savings Plan covers EC2, AWS Fargate, and AWS Lambda?::Compute Savings Plans (up to 66%)

What does an EC2 Instance Savings Plan lock you to, and what is its maximum discount?::One instance family in one Region; up to 72%

Which EC2 option fits per-socket or per-core software licenses (BYOL)?::Dedicated Hosts

What do Dedicated Hosts give that Dedicated Instances do not?::Visibility and control of the physical server, including sockets, cores, and host placement

Which option reserves EC2 capacity in an AZ with no term commitment?::On-Demand Capacity Reservations

How is an On-Demand Capacity Reservation billed?::At the On-Demand rate whether or not instances run in it

Which RI scope reserves capacity?::Zonal Reserved Instances (in the named AZ)

Which RI scope gives AZ flexibility and instance size flexibility but no capacity reservation?::Regional Reserved Instances

What is RI instance size flexibility?::A regional RI discount applies to any size in the same instance family (Linux, default tenancy)

How do RI and Savings Plans discounts behave in AWS Organizations?::They apply to the purchasing account first, then to matching usage in other accounts in the organization

Who can turn off RI and Savings Plans discount sharing?::The management account of the organization

What does data transfer from the internet into AWS cost?::Nothing; inbound data transfer is free

Which data transfers are charged?::Out to the internet; between Regions; between AZs

Which EC2-to-EC2 transfer is free?::Within the same AZ using private IP addresses

Name the S3 pricing dimensions.::Storage; requests and data retrievals; data transfer out; management and analytics features; replication

What are the minimum storage durations for S3 Standard-IA, Glacier Flexible Retrieval, and Glacier Deep Archive?::30 days; 90 days; 180 days

Which storage class has the lowest storage price in AWS?::S3 Glacier Deep Archive

How is Amazon EBS storage billed?::Per GB-month of provisioned size, whether used or not

How are EBS snapshots billed?::Per GB-month stored in S3, incremental after the first snapshot

What are the three AWS Free Tier offer types the exam knows?::Always Free; 12 Months Free; Trials

## 4.2 Billing, budget, and cost management

Which tool estimates the cost of an architecture before you build it?::AWS Pricing Calculator (free, no account needed)

Which tool alerts you when actual or forecasted spend crosses a threshold?::AWS Budgets

Which AWS Budgets types exist?::Cost; usage; RI utilization and coverage; Savings Plans utilization and coverage

What can AWS Budgets actions do automatically?::Apply an IAM policy or SCP, or stop specific EC2 or RDS instances

Which tool visualizes past spend with charts and forecasts future spend?::AWS Cost Explorer

How much history and forecast does Cost Explorer show (reference guide)?::Past 12 months and a forecast of the next 12 months

Which tool gives Reserved Instance and Savings Plans purchase recommendations?::AWS Cost Explorer

Which billing source contains the most comprehensive cost and usage data?::AWS Cost and Usage Report (delivered to S3)

Which service can query the Cost and Usage Report directly in S3 with SQL?::Amazon Athena

What does AWS Billing Conductor produce?::Pro forma bills with custom rates for showback and chargeback; your AWS invoice is unchanged

Which feature uses machine learning to detect unusual spend?::AWS Cost Anomaly Detection

What are the four benefits of consolidated billing?::One bill; easy tracking; combined usage for volume and RI or Savings Plans discounts; no extra fee

How does consolidated billing lower S3 costs across many accounts?::It combines usage so the organization reaches cheaper volume pricing tiers

What are the two types of cost allocation tags?::AWS-generated tags and user-defined tags

What must happen before a tag appears in Cost Explorer or the Cost and Usage Report?::It must be activated as a cost allocation tag in the Billing and Cost Management console

Who can activate cost allocation tags in an organization?::The management account

What prefix do AWS-generated cost allocation tags have?::aws: (user-defined tags appear as user:)

How do activated cost allocation tags appear in the Cost and Usage Report?::As extra columns used to group costs

Which support plans can open account and billing cases?::All plans, including Basic

## 4.3 Technical resources and AWS Support options

Which support plan is free and includes no technical support cases?::Basic

Which is the lowest plan with 24/7 phone, web, and chat access?::Business

Which support plan offers business-hours email access to Cloud Support Associates?::Developer

Which support plans get only core Trusted Advisor checks?::Basic and Developer (service quotas and basic security)

Which is the lowest plan with all Trusted Advisor checks?::Business

What are the response times on Business for general guidance, system impaired, production impaired, and production down?::24 hours; 12 hours; 4 hours; 1 hour

What are Developer's response times?::General guidance under 24 business hours; system impaired under 12 business hours

What is the business-critical system down response time on Enterprise On-Ramp, and on Enterprise?::Under 30 minutes; under 15 minutes

Which plan gives a pool of Technical Account Managers, and which gives a designated one?::Pool: Enterprise On-Ramp; designated: Enterprise

Which plans include the Concierge Support Team for billing and account help?::Enterprise On-Ramp and Enterprise

What is Infrastructure Event Management?::AWS guidance to plan and run a major event such as a launch or migration

How is Infrastructure Event Management offered across plans?::Business pays an extra fee; Enterprise On-Ramp gets one per year; Enterprise includes it

Name the Trusted Advisor check categories.::Cost optimization; performance; security; fault tolerance; service limits; operational excellence

What is the difference between service health and your account health in the AWS Health Dashboard?::Service health is the public status of all services; your account health shows events affecting your resources

Which support plans can use the AWS Health API?::Business, Enterprise On-Ramp, and Enterprise

Who handles reports of abuse such as spam or port scanning from AWS resources?::The AWS Trust and Safety team

Which resource has AWS-written answers to the most common support questions?::AWS Knowledge Center (on re:Post)

Which AWS-managed community Q&A site replaced the AWS Forums?::AWS re:Post

Which resource provides time-tested strategies, guides, and patterns for migrations?::AWS Prescriptive Guidance

What is the difference between ISVs and system integrators in the AWS Partner Network?::ISVs build and sell software; system integrators help customers design, migrate, and build solutions

Name benefits of being an AWS Partner.::Training and certification; partner events; volume discounts; marketing and funding support

Which AWS Marketplace capabilities support cost management and governance?::Charges on the AWS bill; private offers; Private Marketplace approved lists; license entitlement tracking

AWS Professional Services vs AWS Solutions Architects: what is the difference?::Professional Services is a paid AWS team that delivers projects; Solutions Architects advise on architecture design

AWS Managed Services vs AWS IQ: what is the difference?::AMS has AWS operate your infrastructure ongoing; IQ connected you to freelance AWS Certified experts for projects
