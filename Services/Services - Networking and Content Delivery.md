---
tags:
  - clf-c02
  - services
  - services/networking-and-content-delivery
category: "Networking and Content Delivery"
status: not-started
---
# Services: Networking and Content Delivery

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

VPC components, security groups versus network ACLs, and gateways are taught in [[3.5 Network Services]]. Edge locations and global reach are in [[3.2 AWS Global Infrastructure]]; connectivity choices (VPN, Direct Connect, public internet) and deployment models are in [[3.1 Deploying and Operating in the AWS Cloud]]. Network security services (WAF, Shield, Network Firewall) live in [[Services - Security, Identity, and Compliance]].

| Service | What it is | Cue in a question |
|---|---|---|
| [[#Amazon API Gateway]] | Managed front door for APIs | "create, publish, secure REST or WebSocket APIs", "serverless backend with Lambda" |
| [[#Amazon CloudFront]] | Content delivery network (CDN) using edge caching | "cache content close to users", "speed up static and dynamic website globally" |
| [[#AWS Direct Connect]] | Private dedicated line from on premises to AWS | "dedicated", "consistent performance", "does not traverse the internet" |
| [[#AWS Global Accelerator]] | Static anycast IPs over the AWS global network | "static IP addresses", "TCP/UDP", "fast Regional failover", "gaming or VoIP" |
| [[#Amazon Route 53]] | DNS, domain registration, health checks | "domain name", "DNS", "route users by latency or geography" |
| [[#Amazon VPC]] | Your logically isolated virtual network | "isolated network", "subnets", "private network in AWS" |
| [[#AWS VPN]] | Encrypted tunnel over the internet | "encrypted connection over the internet", "quick to set up", "remote workers" |
| [[#AWS Transit Gateway]] | Hub connecting many VPCs and on-premises networks | "connect hundreds of VPCs", "hub and spoke", "simplify peering mesh" |

> [!tip] Two quick splits
> **CloudFront** caches content at edge locations (HTTP/HTTPS). **Global Accelerator** does not cache; it gives static IPs and routes TCP/UDP traffic over the AWS backbone to the best endpoint.
> **Direct Connect** is a private physical link (consistent, not over the internet, weeks to set up). **VPN** is an encrypted tunnel over the public internet (fast and cheap to set up, variable performance).

## Amazon API Gateway

> [!summary] Create, publish, and monitor REST, HTTP, and WebSocket APIs at any scale.

- **What it does:** A fully managed service that acts as the front door for applications to reach backend logic or data, such as AWS Lambda functions, HTTP endpoints, or other AWS services. It handles request routing, authorization, throttling, and monitoring.
- **Choose it when:** The scenario needs to expose a backend (especially Lambda) as a public or private API, build a serverless web or mobile backend, or create real-time two-way WebSocket APIs.
- **Key facts:**
  - API types: REST APIs, HTTP APIs, WebSocket APIs.
  - Classic serverless pattern: API Gateway + Lambda + DynamoDB.
  - Supports throttling, caching, API keys and usage plans, and authorization with IAM, Amazon Cognito, or Lambda authorizers.
  - Pay per API call received and data transferred; no servers to manage.
  - Can be protected by AWS WAF.
- **Don't confuse with:** [[Services - Frontend Web and Mobile#AWS AppSync|AWS AppSync]] (managed GraphQL and pub/sub APIs). [[#Amazon CloudFront]] (caches and delivers content; it does not manage APIs, though it can sit in front of one). [[Services - Compute#Elastic Load Balancing (ELB)|Elastic Load Balancing]] distributes traffic across targets but provides no API management.
- **Docs:** [What is Amazon API Gateway?](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)

## Amazon CloudFront

> [!summary] Speed up distribution of static and dynamic web content to end users through edge locations.

- **What it does:** A content delivery network (CDN). It caches copies of content at edge locations around the world, so users are served from the nearest location with lower latency, and requests that miss the cache go back to the **origin** over the AWS network.
- **Choose it when:** The question is about reducing latency for global users of a website, video, images, or downloads; offloading traffic from an origin server or S3 bucket; or serving content securely over HTTPS at the edge.
- **Key facts:**
  - Origins can be an S3 bucket, an EC2 instance, an Elastic Load Balancer, or any custom HTTP server (including on premises).
  - Uses AWS edge locations, which are separate from Regions and far more numerous.
  - Includes AWS Shield Standard at no extra cost and integrates with AWS WAF for layer 7 filtering.
  - Free TLS certificates through ACM; can restrict S3 access so content is reachable only through CloudFront.
  - Content stays cached for a time to live (TTL); you can invalidate cached objects.
- **Don't confuse with:** [[#AWS Global Accelerator]] (no caching; static IPs; TCP/UDP; for non-HTTP or failover use cases). [[Services - Storage#Amazon S3|Amazon S3]] stores content; CloudFront delivers it faster. [[#Amazon Route 53]] resolves names; it does not deliver content.
- **Docs:** [What is Amazon CloudFront?](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

## AWS Direct Connect

> [!summary] A private dedicated network connection from an on-premises data center to the cloud.

- **What it does:** Provides a dedicated physical network link between your data center or office and AWS through a Direct Connect location, bypassing the public internet.
- **Choose it when:** The scenario needs consistent network performance, predictable low latency, high bandwidth for large ongoing data transfer, or a connection that does not travel over the public internet.
- **Key facts:**
  - Private, but ==not encrypted by default==; for encryption, run an AWS Site-to-Site VPN over Direct Connect (or use MACsec on supported connections).
  - Takes weeks to provision (physical cabling through a Direct Connect location or partner), unlike a VPN.
  - Dedicated connections or hosted connections through AWS Direct Connect Partners.
  - Can reduce data transfer out costs for high-volume traffic.
  - A **Direct Connect gateway** connects to VPCs in multiple Regions.
  - For resilience, use a second Direct Connect link or a VPN as backup.
- **Don't confuse with:** [[#AWS VPN]] (encrypted, over the internet, minutes to set up, less consistent). [[#AWS Global Accelerator]] (improves internet users' access to your app, not a private link from your data center). [[Services - Migration and Transfer#AWS Snow Family|AWS Snow Family]] (offline physical data transfer when the network is too slow).
- **Docs:** [What is AWS Direct Connect?](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)

## AWS Global Accelerator

> [!summary] Improve availability and performance of applications through a global network of endpoints.

- **What it does:** Gives your application two static anycast IP addresses. User traffic enters the AWS global network at the nearest edge location and travels over the AWS backbone (not the public internet) to the healthiest, closest endpoint, such as a load balancer, EC2 instance, or Elastic IP in one or more Regions.
- **Choose it when:** The question needs fixed static IP addresses for a global application, fast automatic failover between Regions, or better performance for non-HTTP traffic (TCP or UDP), such as gaming, IoT, or voice over IP.
- **Key facts:**
  - Uses edge locations, as CloudFront does, but ==does not cache content==.
  - Health checks route traffic away from unhealthy endpoints within seconds, without DNS caching delays.
  - Static IPs simplify allow-listing by clients and firewalls.
  - Works at the network layer (TCP/UDP), not only HTTP.
- **Don't confuse with:** [[#Amazon CloudFront]] caches HTTP(S) content at the edge. [[#Amazon Route 53]] latency or failover routing works through DNS answers, which clients may cache. [[#AWS Direct Connect]] is a private link from your own premises.
- **Docs:** [What is AWS Global Accelerator?](https://docs.aws.amazon.com/global-accelerator/latest/dg/what-is-global-accelerator.html)

## Amazon Route 53

> [!summary] DNS service for domain registration, DNS routing, and health checking.

- **What it does:** A highly available Domain Name System (DNS) service. DNS translates human-readable names such as `example.com` into IP addresses. Route 53 can also register domain names and check the health of endpoints so traffic goes only to healthy resources.
- **Choose it when:** The scenario mentions registering a domain, DNS, routing users to the closest or lowest-latency Region, sending traffic to a backup site when the primary fails, or splitting traffic by percentage.
- **Key facts:**
  - Three jobs: ==domain registration, DNS routing, health checking==.
  - Routing policies: simple, weighted (percentage splits, for example for testing), latency-based, failover (active-passive disaster recovery), geolocation (by user location, for example for content restrictions or localization), geoproximity, multivalue answer, and IP-based.
  - Global service; the name refers to DNS port 53.
  - Route 53 is designed for very high availability (backed by a 100% availability SLA).
- **Don't confuse with:** [[#AWS Global Accelerator]] routes traffic over the AWS network using static IPs, without relying on DNS. [[#Amazon CloudFront]] delivers and caches content. [[Services - Compute#Elastic Load Balancing (ELB)|Elastic Load Balancing]] spreads traffic across targets inside a Region; Route 53 can direct users between Regions.
- **Docs:** [What is Amazon Route 53?](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html)

## Amazon VPC

> [!summary] Launch AWS resources in logically isolated virtual networks.

- **What it does:** Amazon Virtual Private Cloud (VPC) is your own logically isolated section of the AWS Cloud. You choose the IP address range, create subnets, and control routing and security for the resources you launch into it.
- **Choose it when:** The question asks for an isolated network for resources, separating public-facing and private resources, or controlling inbound and outbound traffic at the instance or subnet level.
- **Key facts:** building blocks to recognize (full treatment in [[3.5 Network Services]]):
  - **Subnets**: ranges of IP addresses in one Availability Zone; **public** subnets have a route to an internet gateway, **private** subnets do not.
  - **Gateways**: **internet gateway** (VPC to internet), **NAT gateway** (lets private-subnet instances reach out to the internet without allowing inbound connections), **virtual private gateway** (AWS side of a Site-to-Site VPN), plus Transit Gateway and Direct Connect gateway.
  - **Security groups**: instance-level, **stateful**, allow rules only. **Network ACLs**: subnet-level, **stateless**, allow and deny rules.
  - **Route tables**, **VPC peering** (connect two VPCs privately), **VPC endpoints** (reach AWS services such as S3 privately), and **VPC Flow Logs** (record IP traffic).
  - A VPC spans all Availability Zones in one Region.
  - Configuring VPC security groups and network ACLs is the customer's responsibility.
- **Don't confuse with:** [[#AWS VPN]] and [[#AWS Direct Connect]] connect an on-premises network to a VPC; the VPC is the network itself. [[Services - Security, Identity, and Compliance#AWS Network Firewall|AWS Network Firewall]] adds managed stateful inspection and intrusion prevention for a whole VPC beyond security groups and network ACLs.
- **Docs:** [What is Amazon VPC?](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)

## AWS VPN

> [!summary] Establish a secure and private tunnel from on premises to the cloud.

- **What it does:** Creates encrypted IPsec tunnels over the public internet between your network or users and AWS. It has two parts: **AWS Site-to-Site VPN** (connects an office or data center network to a VPC) and **AWS Client VPN** (connects individual users' devices to AWS or on-premises networks).
- **Choose it when:** The scenario needs an encrypted hybrid connection set up quickly and cheaply, a backup for Direct Connect, or secure remote access for employees.
- **Key facts:**
  - Traffic travels over the internet, so performance varies; it is ==encrypted== in transit.
  - Site-to-Site VPN: a **customer gateway** on premises (your device) connects to a **virtual private gateway** or a **Transit Gateway** on the AWS side; each connection has two tunnels for redundancy.
  - Can be set up in minutes, unlike Direct Connect.
  - Can run over Direct Connect to add encryption.
- **Don't confuse with:** [[#AWS Direct Connect]] (private dedicated link, consistent performance, not over the internet, not encrypted by default, weeks to set up). [[Services - End-User Computing#Amazon WorkSpaces|Amazon WorkSpaces]] gives users a virtual desktop, not a network tunnel.
- **Docs:** [What is AWS Site-to-Site VPN?](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)

## AWS Transit Gateway

> [!summary] Connects Amazon VPCs, AWS accounts, and on-premises networks to a single gateway.

- **What it does:** A regional network hub. Each VPC, VPN connection, or Direct Connect gateway attaches once to the transit gateway, which routes between them, instead of you building a mesh of one-to-one connections.
- **Choose it when:** The question involves connecting many VPCs (possibly across accounts) and on-premises networks, simplifying network management, or replacing a large number of VPC peering connections.
- **Key facts:**
  - Hub-and-spoke design; VPC peering is one-to-one and not transitive, so many VPCs need many peering links.
  - Can be shared with other accounts through AWS RAM.
  - Supports Site-to-Site VPN attachments and Direct Connect.
  - Transit gateways in different Regions can be peered.
- **Don't confuse with:** VPC peering (direct one-to-one link between two VPCs). The **Direct Connect gateway** links a Direct Connect connection to VPCs in multiple Regions. The **virtual private gateway** is the AWS end of a VPN for one VPC. [[#AWS Global Accelerator]] improves user traffic to applications, not network-to-network routing.
- **Docs:** [What is a transit gateway?](https://docs.aws.amazon.com/vpc/latest/tgw/what-is-transit-gateway.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
