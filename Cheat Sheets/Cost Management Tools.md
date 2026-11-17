---
tags:
  - clf-c02
  - cheat-sheet
---
# Cost Management Tools

| Tool | Timing | One line | Cue words |
| --- | --- | --- | --- |
| AWS Pricing Calculator | **Before** | Estimate cost of a planned architecture; free, no account needed | "estimate", "before migrating" |
| AWS Budgets | **During** (proactive) | Alert on actual or **forecasted** cost, usage, RI or SP utilization/coverage; budget actions | "alert", "notify", "threshold" |
| AWS Cost Explorer | **After** (analysis) | Charts of past 12 months + 12-month forecast; RI/SP recommendations | "visualize", "trend", "forecast", "graph" |
| AWS Cost and Usage Report | **After** (raw) | **Most comprehensive** line-item data, hourly/daily/monthly, to S3; query with Athena | "most detailed", "line items", "S3", "Athena" |
| AWS Billing Conductor | Custom | **Pro forma** bills with custom rates for **showback/chargeback** | "reseller", "custom rates", "chargeback" |
| AWS Cost Anomaly Detection | Continuous | ML finds unusual spend, alerts with root cause | "anomaly", "unexpected spike" |
| Billing and Cost Management console | Any | Bills, invoices, payments, credits, Free Tier usage, tag activation, Cost Categories | "invoice", "payment method" |
| CloudWatch billing alarm | During | Alarm on `EstimatedCharges` (us-east-1) | "billing alarm" |
| AWS Trusted Advisor (cost checks) | Any | Finds idle and underused resources | "idle resources", "underutilized" |
| AWS Compute Optimizer | Any | Rightsizing recommendations from utilization | "over-provisioned" |

**Mnemonic: "Calculate, Budget, Explore, Report"** = before, during, after, deepest detail.

## AWS Organizations consolidated billing

- One bill · easy tracking per account · **combined usage for volume discounts** · **shared RI and Savings Plans discounts** · no extra fee.
- Management account pays for all member accounts and can turn off discount sharing.

## Cost allocation tags

| | AWS-generated | User-defined |
| --- | --- | --- |
| Applied by | AWS | You |
| Prefix | `aws:` | `user:` |
| Must activate in Billing console | Yes | Yes |

- Activated by the **management account**; up to 24 hours to appear; not retroactive by default.
- Show as **columns in the CUR** and as **filters in Cost Explorer**; Budgets can filter by tag.
- Apply in bulk with Resource Groups and Tag Editor.

## If the question says X, answer Y

- "Email me when spend is forecast to exceed $X" → **AWS Budgets**
- "Which service cost the most last quarter?" → **AWS Cost Explorer**
- "Most granular billing data", "hourly line items in S3" → **AWS Cost and Usage Report**
- "Estimate cost before building" → **AWS Pricing Calculator**
- "Reseller bills customers with its own rates" → **AWS Billing Conductor**
- "Single bill for many accounts", "volume discounts across accounts" → **AWS Organizations consolidated billing**
- "Track cost by project or department" → **cost allocation tags** (activated) or separate accounts
- "Tag not showing in Cost Explorer" → **activate it** as a cost allocation tag
- "Recommend how many RIs or Savings Plans to buy" → **AWS Cost Explorer**
- "Unusual spend detected by ML" → **AWS Cost Anomaly Detection**

Review: [[4.2 Billing, Budget, and Cost Management]] · [[Services - Cost Management]] · [[EC2 Purchasing Options]] · [[Flashcards - Domain 4]]
