---
tags:
  - clf-c02
  - cheat-sheet
---
# EC2 Purchasing Options

| Option | Commitment | Max discount | Pick it for | Watch out |
| --- | --- | --- | --- | --- |
| On-Demand | None, per second | 0% | Unpredictable, short, can't be interrupted, dev/test | Most expensive shared-tenancy option |
| Standard RI | 1 or 3 yr | 72% | Steady 24/7, config won't change | Can't change family; can sell on RI Marketplace |
| Convertible RI | 1 or 3 yr | 66% | Steady, family may change | Exchange for equal or greater value; can't sell |
| Compute Savings Plan | $/hour for 1 or 3 yr | 66% | Steady spend across EC2 + **Fargate + Lambda**, any Region | Smaller discount than EC2 Instance SP |
| EC2 Instance Savings Plan | $/hour for 1 or 3 yr | 72% | One instance **family** in one **Region** | Locked to that family and Region |
| Spot | None | 90% | Interruptible: batch, big data, CI/CD, rendering | 2-minute interruption notice |
| Dedicated Host | On-Demand or reserved | | **Server-bound licenses (BYOL)**, compliance, see sockets/cores | Costliest |
| Dedicated Instance | None, per second | | Single-tenant hardware, no host control needed | No socket/core visibility |
| On-Demand Capacity Reservation | **None**, any duration | 0% alone | Guarantee capacity in one AZ | Billed On-Demand even if unused; add SP or regional RI for discount |

**Payment options** (RIs and Savings Plans): All Upfront (biggest discount) > Partial Upfront > No Upfront (smallest). 3-year beats 1-year.

**RI flexibility**

| | Regional RI | Zonal RI |
| --- | --- | --- |
| Reserves capacity | No | Yes, in that AZ |
| AZ flexibility | Any AZ in Region | That AZ only |
| Size flexibility | Yes (same family, Linux, default tenancy) | No |

- Modify: AZ, scope, size within family. Exchange (Convertible only): family, OS, tenancy.
- RI Marketplace: sell unused **Standard** RIs; buy third-party RIs with shorter terms.

**AWS Organizations**: one bill; RI and Savings Plans discounts apply to the buyer first, then any matching usage in other accounts; management account can turn sharing off; usage pooled for volume tiers.

**Data transfer**: IN from internet free · OUT to internet charged (first 100 GB/month free) · between Regions charged · between AZs charged · same AZ private IP free.

**Mnemonic: "SPOT stops, RI stays, HOST holds licenses."**

## If the question says X, answer Y

- "Can be interrupted", "flexible start and end", "lowest cost" → **Spot**
- "Steady state", "24/7 for 3 years", "lowest cost, no interruption" → **Standard RI** or **EC2 Instance Savings Plan**
- "May change instance family" → **Convertible RI** or **Compute Savings Plan**
- "Covers Lambda and Fargate too" → **Compute Savings Plan**
- "Per-socket / per-core license", "BYOL", "physical server" → **Dedicated Host**
- "Single-tenant hardware" only → **Dedicated Instance**
- "Guarantee capacity in an AZ, no long-term commitment" → **On-Demand Capacity Reservation**
- "Unknown usage", "short-term, uninterruptible", "new app" → **On-Demand**
- "Sell unused reservation" → **Reserved Instance Marketplace** (Standard only)

Review: [[4.1 AWS Pricing Models]] · [[Compute Picker]] · [[Cost Management Tools]] · [[Flashcards - Domain 4]]
