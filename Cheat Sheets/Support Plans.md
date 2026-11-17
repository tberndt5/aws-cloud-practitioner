---
tags:
  - clf-c02
  - cheat-sheet
---
# Support Plans

| | Basic | Developer | Business | Enterprise On-Ramp | Enterprise |
| --- | --- | --- | --- | --- | --- |
| Tech support | None (account, billing, quotas only) | Business-hours **email** | **24/7 phone, web, chat** | 24/7 phone, web, chat | 24/7 phone, web, chat |
| Trusted Advisor | Core | Core | **All** | All | All |
| General guidance | | < 24 business hrs | < 24 hrs | < 24 hrs | < 24 hrs |
| System impaired | | < 12 business hrs | < 12 hrs | < 12 hrs | < 12 hrs |
| Production impaired | | | < 4 hrs | < 4 hrs | < 4 hrs |
| Production down | | | **< 1 hr** | < 1 hr | < 1 hr |
| Business-critical down | | | | **< 30 min** | **< 15 min** |
| TAM | | | | **Pool** | **Designated** |
| Concierge (billing/account) | | | | Yes | Yes |
| Infrastructure Event Mgmt | | | Extra fee | 1 per year | Included |
| Health API / Support API | | | Yes | Yes | Yes |

Core Trusted Advisor checks = service quotas + basic security.

**Mnemonic: "24-12-4-1, then 30 and 15."** Developer stops after 12 and counts business hours.

Current status: Developer and Business closed to new subscriptions on December 2, 2025; Developer, Business, and Enterprise On-Ramp end January 1, 2027. Current lineup: Basic, Business Support+, Enterprise Support, Unified Operations. Answer exam questions with the five plans above.

## Trusted Advisor categories

Cost optimization · Performance · Security · Fault tolerance · Service limits (+ Operational excellence). Mnemonic: **"C-P-S-F-S"** ("Cheap People Should Fix Stuff").

## Where to get help

| Need | Go to |
| --- | --- |
| Open or track a case | AWS Support Center |
| Common "how do I" answers written by AWS | AWS Knowledge Center (on re:Post) |
| Community Q&A | AWS re:Post |
| Proven migration patterns and step-by-step guides | AWS Prescriptive Guidance |
| Best-practice papers | AWS Whitepapers |
| Report spam, port scans, DoS, phishing from AWS IPs | AWS Trust and Safety (abuse form, abuse@amazonaws.com) |
| AWS events affecting your resources | AWS Health Dashboard (your account health); Health API for automation |
| Status of all AWS services | AWS Health Dashboard (service health) |
| AWS team delivers your project | AWS Professional Services |
| Architecture design help from AWS | AWS Solutions Architects |
| AWS runs your operations | AWS Managed Services (AMS) |
| Hire a certified freelancer | AWS IQ (now shut down) |
| Startup credits | AWS Activate |
| Third-party software on your AWS bill | AWS Marketplace |
| Third-party consultants or software vendors | AWS Partner Network (SIs, ISVs) |

## If the question says X, answer Y

- "Cheapest plan with 24/7 phone" → **Business**
- "Full Trusted Advisor, cheapest" → **Business**
- "15-minute response" or "designated TAM" → **Enterprise**
- "30-minute response" or "pool of TAMs" → **Enterprise On-Ramp**
- "Only billing questions, free" → **Basic**
- "Testing, business-hours email is fine" → **Developer**
- "Billing expert team" → **Concierge** (On-Ramp and Enterprise)
- "Plan for a big launch event" → **Infrastructure Event Management**

Review: [[4.3 Technical Resources and Support Options]] · [[Services - Customer Engagement]] · [[Flashcards - Domain 4]]
