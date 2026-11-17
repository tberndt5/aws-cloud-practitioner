---
tags:
  - clf-c02
  - services
  - services/compute
category: "Compute"
status: not-started
---
# Services: Compute

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Concepts (instance families, elasticity, how much you manage at each level of abstraction) are taught in [[3.3 Compute Services]]. Local Zones and Wavelength also belong to [[3.2 AWS Global Infrastructure]], and EC2 pricing lives in [[4.1 AWS Pricing Models]]. Elastic Load Balancing and Amazon EC2 Auto Scaling are added here because task statement 3.3 asks about load balancers and auto scaling.

Cross-listing: the reference guide puts **AWS Lambda** under Compute, but the exam guide lists it under Serverless; see [[Services - Serverless#AWS Lambda|AWS Lambda]]. Containers (ECS, EKS, ECR) are in [[Services - Containers]].

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#AWS Batch\|AWS Batch]] | Managed scheduling and compute for batch jobs | "batch jobs", "hundreds of thousands of jobs", "run overnight" |
| [[#Amazon EC2\|Amazon EC2]] | Resizable virtual servers you fully control | "virtual machine", "full control of OS", "choose instance type" |
| [[#AWS Elastic Beanstalk\|AWS Elastic Beanstalk]] | Upload code; AWS deploys and runs the environment | "just upload code", "PaaS", "developers don't want to manage infrastructure" |
| [[#Amazon Lightsail\|Amazon Lightsail]] | Simple virtual private servers at fixed monthly price | "simple website", "WordPress", "predictable low monthly price", "little AWS experience" |
| [[#AWS Local Zones\|AWS Local Zones]] | AWS infrastructure placed near large cities | "single-digit millisecond latency for users in a specific metro area" |
| [[#AWS Outposts\|AWS Outposts]] | AWS-managed racks and servers in your data center | "run AWS services on premises", "hybrid", "data residency on site" |
| [[#AWS Wavelength\|AWS Wavelength]] | AWS compute inside telecom 5G networks | "5G", "mobile devices", "ultra-low latency" |
| [[#Elastic Load Balancing (ELB)\|Elastic Load Balancing]] | Spreads incoming traffic across healthy targets | "distribute traffic", "single endpoint", "health checks across AZs" |
| [[#Amazon EC2 Auto Scaling\|Amazon EC2 Auto Scaling]] | Adds and removes EC2 instances with demand | "elasticity", "scale out/in automatically", "replace unhealthy instances" |

> [!tip] Level of control, most to least
> **EC2** (you manage OS and up) → **Lightsail** (simplified EC2 bundles) → **Elastic Beanstalk** (you supply code, AWS builds the environment but you can still see it) → **Lambda** (functions only, no servers). More control means more customer responsibility under the [[2.1 Shared Responsibility Model]].

## AWS Batch

> [!summary] Run batch computing workloads.

- **What it does:** AWS Batch plans, schedules, and runs batch jobs (work that runs to completion without user interaction, such as rendering, simulations, or nightly data processing). You submit jobs to a queue; Batch provisions the right amount and type of compute (EC2, Spot Instances, or Fargate) and shuts it down when jobs finish.
- **Choose it when:** the question says "batch processing", "large numbers of computing jobs", "jobs that can run in the background", or "efficiently run many jobs without managing a cluster".
- **Key facts:**
  - Fully managed job scheduler; no batch software or servers for you to install.
  - Dynamically chooses compute based on job requirements; can use Spot Instances to save cost.
  - No additional charge for Batch itself; you pay for the underlying compute.
- **Don't confuse with:** **Lambda** (short event-driven functions, maximum 15 minutes; Batch suits long-running jobs). **EMR** (Hadoop/Spark big data). **Step Functions** (orchestrates workflow steps; does not provision compute for job queues).
- **Docs:** [What is AWS Batch?](https://docs.aws.amazon.com/batch/latest/userguide/what-is-batch.html)

## Amazon EC2

> [!summary] Provides scalable computing capacity in the AWS Cloud.

- **What it does:** Amazon Elastic Compute Cloud (EC2) gives you virtual servers, called instances, that you launch in minutes from an Amazon Machine Image (AMI, a template with the OS and software). You choose the instance type (CPU, memory, storage, networking), the operating system, and the network, and you have full administrative control.
- **Choose it when:** the question needs a virtual machine, full control of the operating system, custom or legacy software, or a specific instance type for the workload.
- **Key facts:**
  - **Instance families** (see [[3.3 Compute Services]]): general purpose (balanced; web servers), ==compute optimized (CPU-heavy: batch processing, media transcoding, high-performance web servers, gaming servers, scientific modeling)==, memory optimized (large in-memory data sets, in-memory databases), accelerated computing (GPUs or custom chips for ML, graphics), ==storage optimized (high, sequential read/write to local storage: data warehousing, large OLTP databases, distributed file systems)==, and HPC optimized.
  - The customer manages the guest OS (patching), applications, security groups (virtual firewalls), and data; AWS manages the hardware and hypervisor.
  - Storage: **EBS** volumes persist independently of the instance; **instance store** is temporary and lost when the instance stops or terminates.
  - Purchasing options: On-Demand, Reserved Instances, Savings Plans, Spot, Dedicated Hosts, Dedicated Instances, Capacity Reservations (see [[4.1 AWS Pricing Models]]). On-Demand Linux and Windows instances are billed per second (60-second minimum).
- **Don't confuse with:** **Lightsail** (simplified, fixed-price bundles). **Elastic Beanstalk** (deploys your code onto EC2 for you). **Lambda/Fargate** (serverless; no instances to manage).
- **Docs:** [What is Amazon EC2?](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)

## AWS Elastic Beanstalk

> [!summary] Deploy and manage applications without knowledge of the underlying infrastructure.

- **What it does:** Elastic Beanstalk is a platform as a service (PaaS). Developers upload their application code (Java, .NET, PHP, Node.js, Python, Ruby, Go, or Docker), and Beanstalk automatically handles capacity provisioning, load balancing, auto scaling, and health monitoring by creating EC2 instances, a load balancer, and an Auto Scaling group for you.
- **Choose it when:** the question says "developers want to deploy a web application quickly without managing infrastructure", "just upload the code", or "PaaS".
- **Key facts:**
  - ==No additional charge for Elastic Beanstalk==; you pay for the resources it creates (EC2, ELB, and so on).
  - You keep full access to and control over the underlying resources if you need it.
  - Handles deployment, scaling, monitoring, and platform updates.
- **Don't confuse with:** **CloudFormation** (infrastructure as code for any AWS resources; you write the template). **Lightsail** (simple virtual servers, not an application platform). **CodeDeploy** (automates deployments to servers you already manage). **Lambda** (functions, not full web applications on servers).
- **Docs:** [What is AWS Elastic Beanstalk?](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html)

## Amazon Lightsail

> [!summary] Launch projects quickly from a simple management interface.

- **What it does:** Lightsail offers virtual private servers (VPS) and related resources in easy, low-cost bundles. Each plan includes a virtual server, SSD storage, a data transfer allowance, and a static IP for a predictable monthly price, with preconfigured blueprints such as WordPress, LAMP, or Node.js.
- **Choose it when:** the question describes a simple website, blog, small business app, or dev/test environment, a user with little cloud experience, or a need for a "low, predictable monthly price".
- **Key facts:**
  - Fixed monthly pricing bundles; the simplest way to start on AWS.
  - Also offers managed databases, load balancers, containers, and CDN distributions in simplified form.
  - Can connect to the wider AWS environment (for example by VPC peering) as needs grow.
- **Don't confuse with:** **EC2** (full flexibility and pay-per-use pricing). **Elastic Beanstalk** (deploys application code; you don't pick a server bundle).
- **Docs:** [What is Amazon Lightsail?](https://docs.aws.amazon.com/lightsail/latest/userguide/what-is-amazon-lightsail.html)

## AWS Local Zones

> [!summary] Provides low-latency access to applications by placing AWS resources close to large population and industry centers. (Reference guide lists Local Zones under Global Infrastructure.)

- **What it does:** A Local Zone is an extension of an AWS Region placed in a large metropolitan area, away from the Region itself. It runs selected services such as EC2, EBS, and VPC subnets close to end users so latency-sensitive parts of an application respond in single-digit milliseconds.
- **Choose it when:** the question says "users in a specific city need single-digit millisecond latency", "real-time gaming", "media and entertainment content creation", "live video", or "latency-sensitive workloads near a metro area".
- **Key facts:**
  - Each Local Zone is tied to a parent Region; you extend a VPC into it by creating a subnet there.
  - Offers a subset of AWS services; the rest are reached in the parent Region.
  - Also useful for data residency where a Local Zone is in a location with no Region.
- **Don't confuse with:** **Wavelength** (inside 5G carrier networks for mobile devices). **Outposts** (AWS hardware in your own data center). **Edge locations/CloudFront** (cache content; do not run your EC2 instances).
- **Docs:** [What is AWS Local Zones?](https://docs.aws.amazon.com/local-zones/latest/ug/what-is-aws-local-zones.html)

## AWS Outposts

> [!summary] Extends AWS infrastructure, services, APIs, and tools to customer premises.

- **What it does:** Outposts brings AWS-designed hardware into your own data center or on-premises facility as fully managed racks or servers. You run services such as EC2, EBS, ECS, EKS, and RDS locally with the same APIs, console, and tools as in the Region, creating a consistent hybrid experience.
- **Choose it when:** the question says "run AWS services on premises", "low latency access to on-premises systems", "local data processing", "data residency requirements that keep data on site", or "consistent hybrid cloud".
- **Key facts:**
  - AWS delivers, installs, monitors, patches, and maintains the hardware; it connects back to a parent AWS Region.
  - Available as Outposts racks and smaller Outposts servers.
  - The customer provides the physical site: power, networking, and physical security of the facility.
- **Don't confuse with:** **Local Zones** (AWS-operated sites in metro areas, not your building). **Snow Family** (rugged devices for edge computing and data transfer in disconnected locations). **Storage Gateway** (hybrid storage only, not general AWS compute on site).
- **Docs:** [What is AWS Outposts?](https://docs.aws.amazon.com/outposts/latest/userguide/what-is-outposts.html)

## AWS Wavelength

> [!summary] Build applications that deliver ultra-low latencies to mobile devices and end users through 5G networks. (Reference guide lists Wavelength under Global Infrastructure.)

- **What it does:** Wavelength Zones embed AWS compute and storage inside telecommunications providers' data centers at the edge of their 5G networks. Traffic from a mobile device reaches the application without leaving the carrier network, which removes extra network hops to the internet.
- **Choose it when:** the question says "5G", "mobile devices", "ultra-low latency for mobile users", "connected vehicles", "AR/VR", "interactive live video", or "telecommunications carrier".
- **Key facts:**
  - Deployed with communications service providers (for example Verizon in the US).
  - You extend a VPC into a Wavelength Zone and run EC2 instances there.
  - Key phrase to match: ==Wavelength = 5G==.
- **Don't confuse with:** **Local Zones** (metro areas, any users, not specifically 5G). **CloudFront** (content caching at edge locations). **AWS Global Accelerator** (routes traffic over the AWS global network).
- **Docs:** [What is AWS Wavelength?](https://docs.aws.amazon.com/wavelength/latest/developerguide/what-is-wavelength.html)

## Elastic Load Balancing (ELB)

> [!summary] Automatically distributes incoming application traffic across multiple targets, such as EC2 instances, containers, and IP addresses, in one or more Availability Zones. (Not in the reference guide; summary written for this vault.)

- **What it does:** A load balancer is a single point of contact (one DNS name) for clients. It spreads incoming requests across a group of targets, runs health checks, and sends traffic only to healthy targets, which improves availability and fault tolerance.
- **Choose it when:** the question says "distribute traffic across instances", "across multiple Availability Zones", "route traffic only to healthy instances", or "single endpoint for a web tier".
- **Key facts:**
  - **Application Load Balancer (ALB):** layer 7 (HTTP/HTTPS); routes by URL path or host name; for web applications and microservices.
  - **Network Load Balancer (NLB):** layer 4 (TCP/UDP/TLS); ultra-high performance, millions of requests per second, static IP addresses.
  - **Gateway Load Balancer (GWLB):** deploys and scales third-party virtual appliances such as firewalls.
  - **Classic Load Balancer:** previous generation.
  - Scales automatically and works with EC2 Auto Scaling; AWS patches and maintains the load balancers (shared responsibility).
- **Don't confuse with:** **EC2 Auto Scaling** (changes the number of instances; ELB spreads traffic across them; they are used together). **Route 53** (DNS routing, including across Regions; not a load balancer in front of instances). **Global Accelerator** (improves global routing to Regional endpoints using anycast IPs).
- **Docs:** [What is Elastic Load Balancing?](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)

## Amazon EC2 Auto Scaling

> [!summary] Automatically adds or removes EC2 instances to match demand and replaces unhealthy instances. (Not in the reference guide; summary written for this vault.)

- **What it does:** EC2 Auto Scaling manages a group of EC2 instances, called an Auto Scaling group, with a minimum, desired, and maximum size. It launches instances when demand rises (scale out) and terminates them when demand falls (scale in), and it replaces instances that fail health checks.
- **Choose it when:** the question says "elasticity", "automatically adjust capacity", "handle unpredictable traffic", "maintain a fixed number of healthy instances", or "pay only for capacity needed".
- **Key facts:**
  - ==Auto scaling provides elasticity== (task statement 3.3); scaling out/in means adding/removing instances (horizontal scaling).
  - Scaling types: dynamic (target tracking, step, simple, based on CloudWatch metrics), scheduled, and predictive (machine learning forecasts).
  - Uses a launch template to know what to launch; spreads instances across multiple AZs.
  - No additional charge; you pay for the EC2 instances and CloudWatch monitoring.
- **Don't confuse with:** **AWS Auto Scaling** (Management and Governance service that sets scaling plans across several resource types: EC2 Auto Scaling groups, ECS tasks, DynamoDB tables, Aurora replicas; see [[Services - Management and Governance#AWS Auto Scaling|AWS Auto Scaling]]). **ELB** (distributes traffic; does not add instances). Vertical scaling (changing instance size) is not what Auto Scaling does.
- **Docs:** [What is Amazon EC2 Auto Scaling?](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
