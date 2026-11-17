---
tags:
  - clf-c02
  - cheat-sheet
---
# Compute Picker

## Pick the service

| Cue in the question | Answer |
| --- | --- |
| Full control of OS, any software, lift-and-shift a server | Amazon EC2 |
| Run code on events, no servers, short tasks (max 15 min) | AWS Lambda |
| Run containers without managing servers | AWS Fargate (with ECS or EKS) |
| Orchestrate Docker containers, AWS-native | Amazon ECS |
| Kubernetes | Amazon EKS |
| Store container images | Amazon ECR |
| Upload web-app code, AWS handles servers/LB/scaling | AWS Elastic Beanstalk (PaaS) |
| Simple server, predictable monthly price, small site | Amazon Lightsail |
| Large numbers of batch jobs | AWS Batch |
| Compute on premises with AWS APIs | AWS Outposts |
| Low latency in a metro area / over 5G | Local Zones / Wavelength |

Control spectrum: **EC2 (most control) > ECS/EKS on EC2 > Fargate > Elastic Beanstalk > Lambda (least to manage)**

## EC2 instance families

| Family | Cue | Letters |
| --- | --- | --- |
| General purpose | Balanced; web servers, code repos, dev/test | M, T |
| Compute optimized | CPU-heavy: batch, transcoding, HPC, game servers, ML inference | C |
| Memory optimized | Big data in RAM: in-memory DBs, real-time analytics | R, X |
| Storage optimized | Heavy local disk I/O: NoSQL, OLTP, data warehousing | I, D, H |
| Accelerated computing | GPUs/accelerators: ML training, graphics | P, G, Inf, Trn |

AMI = template (OS + software + config) to launch instances. Pricing models → [[EC2 Purchasing Options]] and [[4.1 AWS Pricing Models]].

## Lambda vs Fargate

| | Lambda | Fargate |
| --- | --- | --- |
| Runs | Functions | Containers |
| Trigger | Events | Long-running services or tasks |
| Time limit | 15 minutes | None |

## Scaling and load balancing

- **EC2 Auto Scaling**: min/desired/max instances in a group; adds and removes instances = **elasticity**; replaces unhealthy instances.
- **AWS Auto Scaling**: one place to scale EC2 groups, Spot Fleets, ECS tasks, DynamoDB, Aurora replicas.
- **Elastic Load Balancing**: distributes traffic to healthy targets across AZs.

| Load balancer | Layer | For |
| --- | --- | --- |
| Application (ALB) | 7 | HTTP/HTTPS, path/host routing, microservices |
| Network (NLB) | 4 | TCP/UDP, extreme performance, static IP |
| Gateway (GWLB) | 3 | Third-party firewalls and virtual appliances |

Auto Scaling = **how many**; load balancer = **which one gets the request**.

Links: [[3.3 Compute Services]] · [[Services - Compute]] · [[Services - Containers]] · [[Services - Serverless]] · [[Commonly Confused Services]]
