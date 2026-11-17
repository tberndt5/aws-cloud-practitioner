---
tags:
  - clf-c02
  - services
  - services/serverless
category: "Serverless"
status: not-started
---
# Services: Serverless

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

**Serverless** means you run code or containers without provisioning, patching, or scaling servers; AWS handles the infrastructure, scaling is automatic, and you pay only for what you use. Concepts are in [[3.3 Compute Services]] (task statement 3.3: "recognizing the appropriate use of different serverless compute options (for example, AWS Fargate, Lambda)").

Cross-listing: the reference guide lists **AWS Lambda** under Compute and **AWS Fargate** under Containers; the exam guide puts both under Serverless. Other serverless services you will meet elsewhere include S3, DynamoDB, SQS, SNS, EventBridge, Step Functions, Athena, and Glue.

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#AWS Fargate\|AWS Fargate]] | Serverless compute engine for containers | "run containers without managing servers or EC2 instances" |
| [[#AWS Lambda\|AWS Lambda]] | Run event-driven code without servers | "run code in response to events", "no servers", "pay per request", "short tasks" |

> [!tip] Fargate or Lambda?
> If the workload is a **container** you want to run as a task or long-running service (including anything over 15 minutes), choose **Fargate**. If it is a **function** triggered by an event and finishes within 15 minutes, choose **Lambda**.

## AWS Fargate

> [!summary] Works with Amazon ECS to run containers without the need to manage servers or EC2 instances.

- **What it does:** Fargate is a serverless compute engine for containers. You define the container image and the CPU and memory it needs, and Fargate runs it without you choosing instance types, patching hosts, or scaling a cluster. The reference guide mentions ECS; Fargate also works with Amazon EKS.
- **Choose it when:** the question says "run containers without managing servers", "serverless containers", or "no EC2 instances to provision for ECS/EKS".
- **Key facts:**
  - ==It is a launch type / capacity option for ECS and EKS, not an orchestrator on its own==.
  - Pay for the vCPU and memory your containers request, for the time they run.
  - Each task or pod runs in its own isolated environment; AWS patches the underlying infrastructure.
  - Fargate Spot runs interruption-tolerant tasks at a discount.
- **Don't confuse with:** **ECS/EKS** (the orchestrators that schedule containers; Fargate is where they run). **EC2 launch type** (you manage the instances). **Lambda** (functions, not containers you manage as long-running services).
- **Docs:** [AWS Fargate](https://aws.amazon.com/fargate/)

## AWS Lambda

> [!summary] Run code without the need to provision or manage servers.

- **What it does:** Lambda runs your code (a function) in response to events such as a file uploaded to S3, an HTTP request through API Gateway, a message in SQS, a DynamoDB table change, or an EventBridge schedule. AWS runs, scales, and patches everything underneath; you supply only the code and its settings.
- **Choose it when:** the question says "run code in response to events", "serverless backend", "no servers to manage", "pay only when code runs", or "process files as they arrive in S3".
- **Key facts:**
  - ==Maximum run time is 15 minutes (900 seconds) per invocation==; longer jobs belong on Fargate, Batch, or EC2.
  - Pricing: per request plus duration (compute time, metered in milliseconds) based on memory allocated; no charge when idle.
  - Free tier includes 1 million requests and 400,000 GB-seconds of compute per month.
  - Scales automatically from zero to thousands of concurrent executions.
  - Shared responsibility: AWS patches the OS and runtime used by Lambda; the customer owns the code, its IAM permissions, and the data.
  - Supports many languages (Node.js, Python, Java, .NET, Ruby, and others through custom runtimes); a function can also be packaged as a container image stored in ECR.
- **Don't confuse with:** **EC2** (servers you manage, any run time). **Fargate** (serverless containers, long-running). **Step Functions** (orchestrates several Lambda functions into a workflow). **Elastic Beanstalk** (deploys full web apps onto EC2).
- **Docs:** [What is AWS Lambda?](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
