---
tags:
  - clf-c02
  - practice
  - domain-4
---
# Practice - Domain 4: Billing, Pricing, and Support

15 original questions. Answer each before opening the callout. Review notes: [[4.1 AWS Pricing Models]] · [[4.2 Billing, Budget, and Cost Management]] · [[4.3 Technical Resources and Support Options]]

### Q1
A media company renders video frames overnight. The job can be stopped and resumed at any time without losing work, and the company wants the lowest possible compute cost. Which EC2 purchasing option should it use?

- A. On-Demand Instances
- B. Spot Instances
- C. Standard Reserved Instances
- D. Dedicated Instances

> [!success]- Answer
> **B.** Spot Instances use spare EC2 capacity at up to 90% off On-Demand and suit interruptible, fault-tolerant work.
> - A: On-Demand works but costs far more than Spot.
> - C: Reserved Instances need a 1- or 3-year commitment and suit steady 24/7 workloads, not overnight jobs.
> - D: Dedicated Instances cost more than On-Demand and address single-tenancy, not cost.
>
> Review: [[4.1 AWS Pricing Models]]

### Q2
A company runs a database on EC2 around the clock and expects no change to the instance type for the next three years. The company wants the largest discount. Which option meets this need?

- A. 3-year Standard Reserved Instance with All Upfront payment
- B. 1-year Convertible Reserved Instance with No Upfront payment
- C. On-Demand Capacity Reservation
- D. Spot Instances with a high maximum price

> [!success]- Answer
> **A.** A Standard RI gives the largest RI discount (up to 72%), and the 3-year term with All Upfront payment gives the lowest price.
> - B: Convertible RIs, shorter terms, and No Upfront all give smaller discounts.
> - C: A Capacity Reservation guarantees capacity but gives no discount.
> - D: Spot can be interrupted, which is unacceptable for a production database.
>
> Review: [[4.1 AWS Pricing Models]]

### Q3
A company has steady compute usage today on EC2, but plans to move part of the workload to AWS Lambda and AWS Fargate over the next year and may change Regions. It wants a 1-year commitment discount that follows the usage. Which option should it choose?

- A. EC2 Instance Savings Plan
- B. Standard Reserved Instances
- C. Compute Savings Plan
- D. Dedicated Hosts

> [!success]- Answer
> **C.** Compute Savings Plans apply to EC2 in any family, size, or Region, and also to Fargate and Lambda.
> - A: EC2 Instance Savings Plans are locked to one instance family in one Region and cover EC2 only.
> - B: Standard RIs apply to one EC2 configuration and cannot cover Lambda or Fargate.
> - D: Dedicated Hosts are physical servers for licensing or compliance, not a flexible discount.
>
> Review: [[4.1 AWS Pricing Models]]

### Q4
A company must run software whose license is tied to the number of physical CPU sockets on the server. Which EC2 option lets the company use its existing license?

- A. Dedicated Instances
- B. Dedicated Hosts
- C. On-Demand Instances
- D. Convertible Reserved Instances

> [!success]- Answer
> **B.** Dedicated Hosts give a whole physical server with visibility of sockets and cores, which server-bound (BYOL) licenses need.
> - A: Dedicated Instances are single-tenant but give no socket or core visibility or host control.
> - C: On-Demand Instances run on shared hardware with no host visibility.
> - D: Convertible RIs are a billing discount, not a host type.
>
> Review: [[4.1 AWS Pricing Models]]

### Q5
Which data transfers are charged by AWS? (Select TWO.)

- A. Data uploaded from the internet to an Amazon S3 bucket
- B. Data sent from an EC2 instance in us-east-1 to an EC2 instance in eu-west-1
- C. Data sent between two EC2 instances in the same Availability Zone using private IP addresses
- D. Data sent from an EC2 instance in one Availability Zone to an instance in another Availability Zone in the same Region
- E. Data uploaded from an on-premises server to Amazon EC2 over the internet

> [!success]- Answer
> **B and D.** Transfer between Regions and between Availability Zones is charged.
> - A: Inbound data from the internet is free.
> - C: Same-AZ traffic over private IP addresses is free.
> - E: Inbound data from the internet is free.
>
> Review: [[4.1 AWS Pricing Models]]

### Q6
A company bought a regional Reserved Instance for an m5.xlarge Linux instance. It now runs two m5.large Linux instances in a different Availability Zone of the same Region. What happens to the discount?

- A. The discount is lost because the AZ changed.
- B. The discount applies because regional RIs have AZ and instance size flexibility within the family.
- C. The discount applies only after the company exchanges the RI.
- D. The discount applies, and capacity is also reserved in the new AZ.

> [!success]- Answer
> **B.** A regional RI applies in any AZ of the Region and, for Linux with default tenancy, to any size in the same family; one xlarge covers two large.
> - A: That describes a zonal RI, which is tied to one AZ.
> - C: No exchange is needed, and only Convertible RIs can be exchanged.
> - D: Regional RIs never reserve capacity; only zonal RIs do.
>
> Review: [[4.1 AWS Pricing Models]]

### Q7
A company has 20 AWS accounts in AWS Organizations. Account A bought Reserved Instances it no longer fully uses, and account B runs matching instances at On-Demand rates. What is the result on the consolidated bill?

- A. Account B pays On-Demand rates because RIs belong only to the purchasing account.
- B. The unused RI discount automatically applies to account B's matching usage.
- C. Account A must sell the RIs on the Reserved Instance Marketplace to account B.
- D. The management account must convert the RIs into Savings Plans.

> [!success]- Answer
> **B.** With consolidated billing, RI discounts apply to the purchasing account first, then to matching usage in other accounts, unless the management account turns sharing off.
> - A: Sharing is on by default across the organization.
> - C: No sale is needed; the discount is shared automatically.
> - D: RIs cannot be converted into Savings Plans, and no action is needed.
>
> Review: [[4.1 AWS Pricing Models]]

### Q8
A finance manager wants to receive an email when the company's forecasted AWS spend for the month will exceed $10,000. Which service should be used?

- A. AWS Cost Explorer
- B. AWS Budgets
- C. AWS Cost and Usage Report
- D. AWS Pricing Calculator

> [!success]- Answer
> **B.** AWS Budgets sends alerts when actual or forecasted cost crosses a threshold you set.
> - A: Cost Explorer visualizes and forecasts spend but is not the alerting tool.
> - C: The CUR is a detailed data file delivered to S3, not an alert.
> - D: Pricing Calculator estimates cost before deployment.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q9
A data team wants hourly, line-item billing data for every resource, including cost allocation tag columns, so it can run SQL queries with Amazon Athena. Which source should it use?

- A. AWS Cost Explorer
- B. AWS Billing Conductor
- C. AWS Cost and Usage Report
- D. AWS Trusted Advisor

> [!success]- Answer
> **C.** The AWS Cost and Usage Report is the most comprehensive cost and usage data, delivered to S3 and queryable with Athena.
> - A: Cost Explorer is a visual console tool, not a raw line-item export.
> - B: Billing Conductor creates pro forma bills with custom rates.
> - D: Trusted Advisor gives best-practice recommendations, not billing data.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q10
An AWS Solution Provider resells AWS to its customers and needs to show each customer a bill that uses the provider's own rates and groups of accounts. Which service meets this need?

- A. AWS Organizations consolidated billing
- B. AWS Billing Conductor
- C. AWS Budgets
- D. AWS Marketplace

> [!success]- Answer
> **B.** AWS Billing Conductor creates pro forma bills with custom pricing rules and billing groups for showback and chargeback.
> - A: Consolidated billing produces the real single AWS bill at AWS rates.
> - C: Budgets alerts on spend; it does not produce custom bills.
> - D: Marketplace sells third-party software.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q11
A company tagged all its resources with a `Department` tag, but the tag does not appear as an option in AWS Cost Explorer. What should the company do?

- A. Enable AWS Config rules for tagging.
- B. Activate the tag as a cost allocation tag in the Billing and Cost Management console.
- C. Create an AWS Budgets usage budget.
- D. Upgrade to the Business Support plan.

> [!success]- Answer
> **B.** User-defined tags must be activated as cost allocation tags (by the management account) before they appear in Cost Explorer and the Cost and Usage Report.
> - A: AWS Config tracks resource configuration and compliance, not billing tags.
> - C: A budget does not make tags visible in Cost Explorer.
> - D: Support plans do not control cost allocation tags.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q12
Which are benefits of AWS Organizations consolidated billing? (Select TWO.)

- A. One bill for all member accounts
- B. Free AWS Business Support for all member accounts
- C. Combined usage across accounts for volume pricing discounts
- D. Automatic rightsizing of EC2 instances in member accounts
- E. Each member account receives its own separate invoice to pay

> [!success]- Answer
> **A and C.** Consolidated billing gives one bill, easy tracking, combined usage for volume discounts and shared RI and Savings Plans discounts, at no extra fee.
> - B: Support plans are bought separately; consolidated billing does not include them.
> - D: Rightsizing recommendations come from Compute Optimizer or Cost Explorer, and nothing is automatic.
> - E: The management account pays one bill for all members.
>
> Review: [[4.2 Billing, Budget, and Cost Management]]

### Q13
A company runs production workloads and needs 24/7 phone access to AWS engineers and access to all AWS Trusted Advisor checks. It does not need a Technical Account Manager. Which is the most cost-effective support plan?

- A. Developer
- B. Business
- C. Enterprise On-Ramp
- D. Enterprise

> [!success]- Answer
> **B.** Business is the lowest plan with 24/7 phone, web, and chat access and the full set of Trusted Advisor checks.
> - A: Developer has business-hours email only and core Trusted Advisor checks.
> - C: Enterprise On-Ramp meets the need but costs more and adds a TAM pool that is not required.
> - D: Enterprise costs the most and adds a designated TAM.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q14
A company's revenue depends on a trading platform. It needs a response within 15 minutes when that business-critical system is down and wants a designated Technical Account Manager. Which support plan is required?

- A. Business
- B. Enterprise On-Ramp
- C. Enterprise
- D. Developer

> [!success]- Answer
> **C.** Only Enterprise gives a 15-minute business-critical response and a designated TAM.
> - A: Business's fastest response is under 1 hour for production system down, with no TAM.
> - B: Enterprise On-Ramp gives a 30-minute response and a pool of TAMs.
> - D: Developer has no production severities and no TAM.
>
> Review: [[4.3 Technical Resources and Support Options]]

### Q15
A website owner notices repeated port scans and spam coming from IP addresses that belong to AWS. What should the owner do?

- A. Open a technical case in the AWS Support Center under a Business Support plan.
- B. Report the activity to the AWS Trust and Safety team.
- C. Post the issue on AWS re:Post.
- D. Enable AWS Shield Advanced on the website.

> [!success]- Answer
> **B.** The AWS Trust and Safety team handles reports of abuse originating from AWS resources, and anyone can report it through the abuse form or abuse@amazonaws.com.
> - A: Support cases help with your own account; no paid plan is needed to report abuse.
> - C: re:Post is a community Q&A site, not an abuse channel.
> - D: Shield protects against DDoS on your resources but does not report abuse by others.
>
> Review: [[4.3 Technical Resources and Support Options]]
