---
tags:
  - clf-c02
  - cheat-sheet
---
# Networking and Gateways

Back to: [[3.5 Network Services]] · Related: [[3.1 Deploying and Operating in the AWS Cloud]], [[3.2 AWS Global Infrastructure]], [[Global Infrastructure]]

## The six gateways (AWS reference guide wording)

| Gateway | Definition | Hook |
|---|---|---|
| Internet gateway | VPC component that allows communication between a user's computer and the internet | Two-way door; makes a subnet public |
| NAT gateway | Gives instances in a private subnet the ability to connect to services outside the VPC | Outbound only; sits in a public subnet |
| Virtual private gateway | Gateway on the **AWS side** of a Site-to-Site VPN | AWS end of the tunnel |
| Customer gateway | Physical or software appliance the user owns and manages **on premises** | Your end of the tunnel |
| AWS Transit Gateway | Connects VPCs, accounts, and on-premises networks to a single gateway | Hub and spoke |
| Direct Connect gateway | Connectivity that spans VPCs in **multiple Regions** | One DX link, many Regions |

Not a network gateway: **Amazon API Gateway** (create, publish, monitor REST, HTTP, WebSocket APIs).

## VPC parts

| Part | One line |
|---|---|
| VPC | Logically isolated network in one Region, spans its AZs |
| Subnet | IP range in **one AZ**; public (route to IGW) or private (no route to IGW) |
| Route table | Rules that decide where subnet traffic goes |
| VPC peering | Private link between two VPCs; **not transitive** |
| VPC endpoint | Private access to AWS services (S3, DynamoDB, others) without internet or NAT |

## Security group vs network ACL

| | Security group | Network ACL |
|---|---|---|
| Level | Instance (network interface) | Subnet |
| State | **Stateful** | **Stateless** |
| Rules | Allow only | Allow **and deny** |
| Order | All evaluated | Numbered, first match wins |
| Default | Deny all in, allow all out | Default NACL allows all |

Mnemonic: **S**G = **S**tateful, **S**ingle instance. **N**ACL = **N**ot stateful, **N**etwork subnet, can say **N**o.

## Connecting to AWS

| Need | Answer |
|---|---|
| Encrypted tunnel from the data center, quick and cheap | AWS Site-to-Site VPN (over the internet) |
| Remote employees' laptops need secure access | AWS Client VPN |
| Private, dedicated, consistent performance, bypass internet | AWS Direct Connect (weeks to set up; not encrypted by default) |
| Encrypted and private | VPN running over Direct Connect |
| Highly available hybrid link | Direct Connect primary + Site-to-Site VPN backup |
| Many VPCs + on premises through one hub | AWS Transit Gateway |

## Edge and DNS

| | CloudFront | Global Accelerator | Route 53 |
|---|---|---|---|
| What | CDN, **caches** at edge locations | Routes TCP/UDP over AWS backbone, **no caching** | DNS |
| Signature | Distribution, origins (S3, ELB) | **Two static anycast IPs** | Domain registration, DNS routing, health checks |
| Cue | Faster static/dynamic web content worldwide | Gaming, VoIP, fixed IPs, fast Regional failover | Register domain, failover, latency or geo routing |

Route 53 routing policies: Simple · Weighted (percent split) · Latency · Failover (active-passive) · Geolocation (by user location) · Geoproximity (by distance with bias) · Multivalue answer · IP-based.

## If the question says X, answer Y

- "Private subnet instances need to download patches" → NAT gateway
- "Allow internet access to a public subnet" → internet gateway + route table entry
- "Block a specific IP address" → network ACL
- "Stateful firewall for an EC2 instance" → security group
- "On-premises VPN device" → customer gateway
- "Dedicated connection, consistent latency" → Direct Connect
- "Connect thousands of VPCs simply" → Transit Gateway
- "Cache content close to users" → CloudFront
- "Static IP addresses for a global app" → Global Accelerator
- "Route users to the lowest-latency Region" → Route 53 latency routing
- "Fail over to a standby site when health checks fail" → Route 53 failover routing
- "Create a REST API in front of Lambda" → API Gateway
- "Reach S3 from a VPC without the internet" → VPC endpoint
