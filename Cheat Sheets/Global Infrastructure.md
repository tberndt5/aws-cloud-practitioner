---
tags:
  - clf-c02
  - cheat-sheet
---
# Global Infrastructure

## The pieces (reference guide wording)

| Component | Definition | Key fact |
| --- | --- | --- |
| Region | Isolated geographic area that consists of multiple AZs | Minimum 3 AZs; most services are Regional |
| Availability Zone | One or more data centers within a Region | Redundant power/network; within 100 km (60 mi) of each other; no shared single points of failure |
| Edge location | Worldwide network of data centers that optimizes latency and throughput to users | Used by CloudFront, Global Accelerator, Route 53; far more of them than Regions; no EC2 |
| Local Zone | AWS resources close to large population and industry centers | Extension of a Region into a metro area |
| Wavelength Zone | Ultra-low latency to mobile devices through 5G networks | AWS compute inside telecom 5G networks |
| Outposts | AWS infrastructure, services, APIs, tools on customer premises | Your data center, AWS-managed hardware |

Hierarchy: **Region > AZ > data center(s)**. Edge locations sit outside, connected by the AWS backbone.

## Choosing a Region: C-L-A-P

**C**ompliance / data sovereignty (decides first) · **L**atency to users · **A**vailability of services · **P**ricing

## Which level of resilience?

| Need | Answer |
| --- | --- |
| Survive a data center or AZ failure | Multiple AZs (ELB + Auto Scaling, RDS Multi-AZ) |
| Survive a whole-Region outage | Multiple Regions (disaster recovery) |
| Keep each country's data in-country | One Region per jurisdiction |
| Low latency for a global audience | Multiple Regions and/or CloudFront |

## Edge services

| | CloudFront | Global Accelerator |
| --- | --- | --- |
| Does | Caches content (CDN) | Routes traffic over the AWS backbone |
| Caching | Yes | No |
| Traffic | HTTP/HTTPS | TCP/UDP |
| Gives you | Faster static/dynamic web delivery | 2 static anycast IPs, fast Regional failover |

## If the question says X, answer Y

- "One or more data centers" → Availability Zone
- "Isolated geographic area with multiple AZs" → Region
- "Cache content close to users" → CloudFront at edge locations
- "Static IP addresses for a global app", "gaming/VoIP over TCP/UDP" → Global Accelerator
- "Single-digit ms latency for users in a specific city" → Local Zones
- "5G", "mobile devices", "telecom" → Wavelength
- "Run AWS services in our own data center" → Outposts
- "Data must stay in country X" → choose a Region in country X
- "Highly available" → at least two AZs, never one large instance

Links: [[3.2 AWS Global Infrastructure]] · [[3.1 Deploying and Operating in the AWS Cloud]] · [[3.5 Network Services]] · [[Networking and Gateways]]
