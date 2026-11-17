---
tags:
  - clf-c02
  - services
  - services/containers
category: "Containers"
status: not-started
---
# Services: Containers

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

A **container** packages an application with everything it needs (code, runtime, libraries) so it runs the same way anywhere; Docker is the common format. An **orchestrator** starts, stops, places, and scales many containers. Concepts are in [[3.3 Compute Services]] (task statement 3.3: "recognizing the appropriate use of different container options").

Cross-listing: the reference guide lists **AWS Fargate** under Containers; the exam guide lists it under Serverless. See [[Services - Serverless#AWS Fargate|AWS Fargate]].

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#Amazon Elastic Container Registry (Amazon ECR)\|Amazon ECR]] | Managed registry to store container images | "store Docker images", "container image repository" |
| [[#Amazon Elastic Container Service (Amazon ECS)\|Amazon ECS]] | AWS-native container orchestration | "run Docker containers", "AWS-native orchestration", "simplest way to run containers" |
| [[#Amazon Elastic Kubernetes Service (Amazon EKS)\|Amazon EKS]] | Managed Kubernetes control plane | "Kubernetes", "open-source orchestration", "portable across clouds/on premises" |

> [!tip] How they fit together
> Build an image → store it in **ECR** → run it with **ECS** or **EKS** → choose where the containers run: on **EC2 instances you manage** or on **Fargate** (serverless, no instances).

## Amazon Elastic Container Registry (Amazon ECR)

> [!summary] Container image registry that is secure, scalable, and reliable.

- **What it does:** ECR is a fully managed registry where you store, manage, and share container images (Docker and OCI images). ECS, EKS, and Lambda (container image functions) pull images directly from it.
- **Choose it when:** the question says "store container images", "private Docker registry", or "image repository for ECS/EKS".
- **Key facts:**
  - Fully managed; no registry servers to run. Images are stored durably (backed by S3).
  - Private repositories controlled with IAM; ECR Public for publicly shared images.
  - Can scan images for software vulnerabilities (integrates with Amazon Inspector).
  - Pay for storage and data transfer.
- **Don't confuse with:** **ECS/EKS** (run containers; ECR only stores images). **CodeArtifact** (stores software packages such as npm or Maven libraries, not container images). **S3** (general object storage).
- **Docs:** [What is Amazon ECR?](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html)

## Amazon Elastic Container Service (Amazon ECS)

> [!summary] Deploy, manage, and scale containerized applications.

- **What it does:** ECS is AWS's own fully managed container orchestration service. You describe your containers in a task definition, and ECS runs and scales them as tasks and services across a cluster, integrated with ELB, IAM, CloudWatch, and other AWS services.
- **Choose it when:** the question says "run Docker containers on AWS" with no mention of Kubernetes, "AWS-native container orchestration", or "deeply integrated with AWS services".
- **Key facts:**
  - ==Two launch types: EC2 (you manage the container instances) or Fargate (serverless, AWS manages the servers)==.
  - No charge for the ECS control plane; you pay for the EC2 instances or Fargate resources used.
  - Named in task statement 1.4 as an example of a managed AWS service.
- **Don't confuse with:** **EKS** (choose when the question says Kubernetes). **Fargate** (not an orchestrator; it is the serverless compute that ECS or EKS can run containers on). **Elastic Beanstalk** (can deploy Docker apps but is an app platform, not an orchestrator). **ECR** (stores images).
- **Docs:** [What is Amazon ECS?](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)

## Amazon Elastic Kubernetes Service (Amazon EKS)

> [!summary] Run Kubernetes without the need to install, operate, or maintain the Kubernetes control plane or nodes.

- **What it does:** EKS is a managed Kubernetes service. Kubernetes is the popular open-source container orchestration system. AWS runs and scales the Kubernetes control plane across multiple Availability Zones; your containers (pods) run on EC2 nodes or on Fargate.
- **Choose it when:** the question mentions **Kubernetes**, wants to migrate existing Kubernetes workloads, or wants open-source, portable orchestration that also runs on premises or in other environments.
- **Key facts:**
  - Certified Kubernetes-conformant: standard Kubernetes tools and applications work unchanged.
  - Control plane is managed and highly available across AZs; you pay per cluster per hour plus the compute.
  - Worker nodes can be EC2 (self-managed or managed node groups) or Fargate; EKS Anywhere and EKS on Outposts extend it on premises.
  - Named in task statement 1.4 as an example of a managed AWS service.
- **Don't confuse with:** **ECS** (AWS-proprietary orchestrator; simpler; no Kubernetes). **Fargate** (serverless compute for pods/tasks, not an orchestrator).
- **Docs:** [What is Amazon EKS?](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
