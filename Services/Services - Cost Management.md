---
tags:
  - clf-c02
  - services
  - services/cost-management
category: "Cost Management"
status: not-started
---
# Services: Cost Management

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Concepts (consolidated billing, cost allocation tags, pricing models) are taught in [[4.1 AWS Pricing Models]] and [[4.2 Billing, Budget, and Cost Management]]. One-page summary: [[Cost Management Tools]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#AWS Billing Conductor]] | Custom pro forma billing for showback and chargeback | "Partner or reseller", "custom rates", "chargeback/showback", "billing groups" |
| [[#AWS Budgets]] | Budgets with alerts on actual or forecasted spend | "Alert me when", "threshold", "forecasted to exceed", "notify" |
| [[#AWS Cost and Usage Report]] | Most detailed cost and usage data, delivered to S3 | "Most comprehensive / most granular", "line item", "hourly", "query with Athena" |
| [[#AWS Cost Explorer]] | Visualize past costs and forecast future spend | "Visualize", "graph", "trends", "past 12 months", "forecast" |
| [[#AWS Marketplace]] | Catalog of third-party software, data, and services | "Third-party software", "buy a license", "AMI from a vendor", "pay on AWS bill" |
| [[#AWS Pricing Calculator]] | Free tool to estimate cost before building | "Estimate", "before migrating", "planned architecture", "no account yet" |

> [!tip] The time-direction trick
> **Pricing Calculator** = future, for workloads not yet running. **Budgets** = future, alerts against a plan. **Cost Explorer** = past plus a forecast, visual. **Cost and Usage Report** = past, raw line-item detail. **Billing Conductor** = re-priced copy of the bill for someone else.

## AWS Billing Conductor

> [!summary] Custom billing service that can support showback and chargeback workflows of AWS Solution Providers and Enterprise customers.

- **What it does:** Lets you build a second, "pro forma" version of your AWS costs using your own pricing plans, pricing rules (markups or discounts), and custom line items. Accounts are grouped into billing groups, and each group sees costs at the rates you configured. It is built for AWS Channel Partners who resell AWS and for enterprises that charge internal teams.
- **Choose it when:** A reseller or partner needs to bill its own customers at negotiated rates, or a company needs showback (showing a team its costs) or chargeback (actually billing the team's budget) with custom rates.
- **Key facts:**
  - Pro forma data is separate from billable data. ==It does not change the invoice AWS sends you== or how credits, Reserved Instances, and Savings Plans apply.
  - Core objects: billing groups, pricing plans, pricing rules, custom line items.
  - Billing group members can view their pro forma costs in Cost Explorer, Cost and Usage Reports, and Budgets.
  - Works on top of an AWS Organizations structure.
- **Don't confuse with:** [[Services - Management and Governance#AWS Organizations|AWS Organizations]] consolidated billing (one real combined bill, volume discounts) versus Billing Conductor (a custom re-priced view). Cost allocation tags group costs on the real bill; Billing Conductor changes the rates shown.
- **Docs:** [What is AWS Billing Conductor?](https://docs.aws.amazon.com/billingconductor/latest/userguide/what-is-billingconductor.html)

## AWS Budgets

> [!summary] Set a monthly cost budget with alerts for actual spend or forecasted spend.

- **What it does:** You set a budget amount for cost, usage, or commitment coverage, and AWS Budgets notifies you when actual or forecasted values cross a threshold you choose. Budget actions can also respond automatically, for example by applying an IAM policy or SCP that blocks new resources.
- **Choose it when:** The question asks to be alerted or notified before or when spend crosses a limit, or to take an automatic action at a threshold.
- **Key facts:**
  - Six budget types: cost, usage, RI utilization, RI coverage, Savings Plans utilization, Savings Plans coverage.
  - Alerts on ==actual or forecasted== amounts; notifications go to email and/or Amazon SNS topics.
  - Budget actions can apply IAM policies or service control policies, or target specific EC2/RDS instances.
  - Data updates up to three times a day, so alerts are not real time.
  - Budgets can be filtered by service, account, tag, Region, and more; monthly, quarterly, annual, or custom periods.
- **Don't confuse with:** [[#AWS Cost Explorer]] (analyze and visualize, no alerting). Amazon CloudWatch billing alarms also alert on estimated charges, but Budgets is the purpose-built answer for budget thresholds and forecasts.
- **Docs:** [Managing your costs with AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)

## AWS Cost and Usage Report

> [!summary] Contains the most comprehensive set of cost and usage data available.

- **What it does:** Publishes detailed billing data, one line item per combination of product, usage type, and operation, to an Amazon S3 bucket you own. Reports can be broken down by hour, day, or month and by resource or by your cost allocation tags. You analyze it with Amazon Athena, Amazon Redshift, or Amazon QuickSight.
- **Choose it when:** The question says "most detailed", "most comprehensive", "line-item", "hourly granularity", or wants to load raw billing data into an analytics tool.
- **Key facts:**
  - Delivered to ==an S3 bucket== in CSV (or Parquet) files, updated at least once a day.
  - Includes cost allocation tag columns, so activated tags appear in the report (exam guide 4.2 ties tags to CUR).
  - Integrates with Athena (SQL queries), Redshift, and QuickSight for dashboards.
  - Cost Explorer uses the same underlying dataset, but CUR is the raw, most granular form.
- **Don't confuse with:** [[#AWS Cost Explorer]] (visual console, summarized) versus CUR (raw files in S3). [[#AWS Billing Conductor]] can produce a CUR per billing group, but it is the pro forma tool, not the report.
- **Docs:** [What are AWS Cost and Usage Reports?](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html)

Current status: AWS now delivers CUR through AWS Data Exports, where Cost and Usage Report 2.0 (CUR 2.0) is the recommended format and the original report is labeled "Legacy CUR".

## AWS Cost Explorer

> [!summary] Visualize cost and usage over time, including the past 12 months and a forecast of the next 12 months.

- **What it does:** A console tool with graphs and reports that let you filter and group costs by service, account, tag, Region, and more. It shows trends, forecasts future spend, and gives Reserved Instance and Savings Plans purchase recommendations and utilization/coverage reports.
- **Choose it when:** The question asks to visualize, explore, or analyze spending trends, find which service drives costs, or see a forecast in a graph.
- **Key facts:**
  - Exam version: ==past 12 months of data and a 12-month forecast== (reference guide wording).
  - Viewing in the console is free; the Cost Explorer API charges per request.
  - Gives RI and Savings Plans recommendations, plus utilization and coverage reports.
  - Data refreshes at least every 24 hours.
- **Don't confuse with:** [[#AWS Budgets]] (alerts) and [[#AWS Cost and Usage Report]] (raw files). Rightsizing EC2 based on utilization metrics points to [[Services - Management and Governance#AWS Compute Optimizer|AWS Compute Optimizer]].
- **Docs:** [Analyzing your costs with AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)

Current status: The Cost Explorer user guide now states up to 13 months of history and an 18-month forecast; answer "12 and 12" if the exam uses the reference guide wording.

## AWS Marketplace

> [!summary] Curated digital catalog of third-party software, data, and services.

- **What it does:** A store where you find, buy, and deploy software from independent software vendors (ISVs), including AMIs, SaaS products, containers, machine learning models, data products, and professional services. Charges appear on your AWS bill.
- **Choose it when:** A company wants to buy or deploy third-party software (for example a security appliance or firewall) quickly, use an existing vendor license, or pay for third-party products through its AWS bill.
- **Key facts:**
  - Exam guide 2.4: ==third-party security products are available from AWS Marketplace==.
  - Exam guide 4.3: Marketplace offers cost management, governance, and entitlement features (for example, private marketplaces that limit which products employees can buy, and license tracking).
  - Pricing models include free trials, hourly, monthly, annual, BYOL (bring your own license), and private offers negotiated with the seller.
  - Billing is consolidated on the AWS invoice.
- **Don't confuse with:** [[Services - Management and Governance#AWS Service Catalog|AWS Service Catalog]] (your own approved catalog of IT products for internal users) and [[Services - Analytics#AWS Data Exchange|AWS Data Exchange]] (subscribing to third-party data sets specifically). The AWS Partner Network is the partner program; Marketplace is the store.
- **Docs:** [What is AWS Marketplace?](https://docs.aws.amazon.com/marketplace/latest/buyerguide/what-is-marketplace.html)

## AWS Pricing Calculator

> [!summary] Free web-based planning tool to create cost estimates for AWS services before you use them. (No one-line summary in the reference guide.)

- **What it does:** You model a planned architecture by choosing services and configurations, and the calculator shows estimated upfront, monthly, and annual costs. Estimates can be grouped, saved as a shareable link, and exported.
- **Choose it when:** The workload does not exist yet: estimating migration costs, comparing purchase options for a planned design, or building a business case.
- **Key facts:**
  - ==Free==, and you do not need AWS experience to use it (calculator.aws).
  - Save a link to share an estimate, or export to CSV or PDF.
  - Shows the calculation behind each estimate; taxes are not included.
  - Named in the exam guide (task 4.2 and the appendix).
- **Don't confuse with:** [[#AWS Cost Explorer]] (actual past spend and forecasts based on real usage). The calculator estimates costs for something not yet running; Cost Explorer reports on what is already running.
- **Docs:** [What is AWS Pricing Calculator?](https://docs.aws.amazon.com/pricing-calculator/latest/userguide/what-is-pricing-calculator.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
