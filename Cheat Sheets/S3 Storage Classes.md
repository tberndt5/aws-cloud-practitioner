---
tags:
  - clf-c02
  - cheat-sheet
---
# S3 Storage Classes

Back to: [[3.6 Storage Services]] · Related: [[Storage Picker]], [[4.1 AWS Pricing Models]]

Figures from the [Amazon S3 User Guide storage class comparison](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html) and [archive retrieval options](https://docs.aws.amazon.com/AmazonS3/latest/userguide/restoring-objects-retrieval-options.html). **Every class: 99.999999999% (11 nines) durability.**

## The table

| Class | Access pattern | Availability | AZs | Min duration | Retrieval time | Retrieval fee |
|---|---|---|---|---|---|---|
| S3 Standard | Frequent | 99.99% | ≥3 | None | ms | No |
| S3 Intelligent-Tiering | Unknown or changing | 99.9% | ≥3 | None | ms (optional archive tiers: min–hours) | No (small per-object monitoring fee) |
| S3 Standard-IA | Monthly, needs fast access | 99.9% | ≥3 | 30 days | ms | Yes |
| S3 One Zone-IA | Monthly, **re-creatable** | 99.5% | **1** | 30 days | ms | Yes |
| S3 Glacier Instant Retrieval | Quarterly, needs **ms** | 99.9% | ≥3 | 90 days | ms | Yes |
| S3 Glacier Flexible Retrieval | Yearly | 99.99% (after restore) | ≥3 | 90 days | Expedited 1–5 min · Standard 3–5 h · Bulk 5–12 h | Yes (Bulk free) |
| S3 Glacier Deep Archive | Less than yearly, 7–10 yr retention | 99.99% (after restore) | ≥3 | **180 days** | Standard ≤12 h · Bulk ≤48 h (no Expedited) | Yes |
| S3 on Outposts | Data must stay on premises | — | Your Outpost | — | Local | — |

Minimum billable object size: 128 KB for Standard-IA, One Zone-IA, and Glacier Instant Retrieval.

## Memory aids

- Minimum durations: **IA 30 · Glacier 90 · Deep 180**. Standard and Intelligent-Tiering: none.
- Availability ladder: **four 9s** for Standard (and restored Flexible/Deep), **three 9s** for Intelligent-Tiering, Standard-IA, Glacier IR, **99.5** for One Zone.
- "One Zone" is the only class in this table that is not resilient to losing an AZ.
- Cheapest storage: Deep Archive. Cheapest that still returns in milliseconds for rarely used data: Glacier Instant Retrieval.

## If the question says X, answer Y

- "Frequently accessed", "default", "hot data" → S3 Standard
- "Unpredictable or unknown access", "optimize automatically" → S3 Intelligent-Tiering
- "Infrequent but fast when needed", "backups", "disaster recovery copy" → S3 Standard-IA
- "Can be re-created", "secondary copy", "lowest cost IA" → S3 One Zone-IA
- "Archive, rarely accessed, must be immediate (ms)" → S3 Glacier Instant Retrieval
- "Archive, minutes to hours is fine", "free bulk retrieval" → S3 Glacier Flexible Retrieval
- "Compliance retention for years, 12–48 hours is fine", "replace tape", "lowest cost" → S3 Glacier Deep Archive
- "Move data between classes on a schedule" → S3 Lifecycle policy (transition and expiration)
- "Protect against accidental delete" → S3 Versioning
- "Copy to another Region automatically" → S3 Cross-Region Replication (needs versioning)
- "Cannot be deleted or changed for N years" → S3 Object Lock

Current status: S3 Express One Zone (single AZ, single-digit ms, 99.95% availability) was added after the 2023 exam guide.
