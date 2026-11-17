---
tags:
  - clf-c02
  - services
  - services/application-integration
category: "Application Integration"
status: not-started
---
# Services: Application Integration

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

These services let application components talk to each other without being tightly coupled (decoupling: one part can fail, slow down, or scale without breaking the others). Concepts are in [[3.8 Other In-Scope Service Categories]]; task statement 3.8 asks you to "choose the appropriate service to deliver messages and to send alerts and notifications".

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#Amazon EventBridge\|Amazon EventBridge]] | Serverless event bus that routes events by rules | "event-driven", "react to events from AWS services or SaaS apps", "schedule" |
| [[#Amazon Simple Notification Service (Amazon SNS)\|Amazon SNS]] | Pub/sub push notifications to many subscribers | "notify", "alert", "fan out", "email/SMS to subscribers" |
| [[#Amazon Simple Queue Service (Amazon SQS)\|Amazon SQS]] | Message queue that buffers work between components | "decouple", "queue", "buffer", "process later", "poll" |
| [[#AWS Step Functions\|AWS Step Functions]] | Visual workflows that coordinate multiple steps/services | "orchestrate", "workflow", "sequence of Lambda functions", "state machine" |

> [!tip] Push vs pull vs route vs orchestrate
> **SNS pushes** one message to many subscribers. **SQS holds** messages until a consumer **pulls** them. **EventBridge routes** events to targets based on rules. **Step Functions orchestrates** an ordered workflow with branches, retries, and waits.

## Amazon EventBridge

> [!summary] Use events to connect application components together, build scalable event-driven applications.

- **What it does:** EventBridge is a serverless event bus. Events (a change in state, such as "EC2 instance stopped" or "order placed") arrive from AWS services, your own applications, or supported SaaS partners. Rules match events and send them to targets such as Lambda, SQS, SNS, or Step Functions.
- **Choose it when:** the question says "event-driven architecture", "respond automatically when something happens in an AWS service", "integrate with SaaS applications", or "run a task on a schedule (cron)".
- **Key facts:**
  - Serverless, pay per event; no infrastructure.
  - Rules filter events by content and route them to one or more targets.
  - Receives events from many AWS services automatically, plus third-party SaaS event sources.
  - Can also trigger targets on a schedule (EventBridge Scheduler, cron-style).
  - EventBridge grew out of Amazon CloudWatch Events; older questions may still say "CloudWatch Events".
- **Don't confuse with:** **SNS** (pushes messages to subscribers; no content-based routing from SaaS sources). **CloudWatch** (metrics and alarms; an alarm can trigger actions, but event routing is EventBridge). **CloudTrail** (records API calls for auditing).
- **Docs:** [What is Amazon EventBridge?](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)

## Amazon Simple Notification Service (Amazon SNS)

> [!summary] Provides message delivery from publishers to subscribers.

- **What it does:** SNS is a fully managed publish/subscribe (pub/sub) service. A publisher sends a message to an SNS **topic**, and SNS immediately pushes a copy to every subscriber of that topic. Subscribers can be applications (SQS queues, Lambda functions, HTTP/S endpoints) or people (email, SMS text, mobile push notifications).
- **Choose it when:** the question says "send alerts or notifications", "notify administrators by email or SMS", "push", "fan out one message to multiple systems", or "CloudWatch alarm notification".
- **Key facts:**
  - ==Push-based, one-to-many (pub/sub)==; messages are not stored for later retrieval.
  - Topic → subscriptions; protocols include email, SMS, mobile push, HTTP/S, SQS, Lambda.
  - **Fan-out pattern:** SNS topic delivers to several SQS queues so each system processes the message independently.
  - CloudWatch alarms and AWS Budgets alerts commonly notify through SNS.
- **Don't confuse with:** **SQS** (pull-based queue; one consumer processes each message; messages wait until processed). **Amazon SES** (sends formatted marketing or transactional email to any address; SNS email is plain notifications to subscribed endpoints). **EventBridge** (rule-based routing of events).
- **Docs:** [What is Amazon SNS?](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

## Amazon Simple Queue Service (Amazon SQS)

> [!summary] Provides a queue to integrate and decouple distributed software systems and components.

- **What it does:** SQS is a fully managed message queue. A producer puts messages into the queue, and consumers poll the queue and process messages at their own pace. If consumers are slow or offline, messages wait safely in the queue instead of being lost.
- **Choose it when:** the question says "decouple", "buffer requests", "absorb spikes in traffic", "process asynchronously", "messages must not be lost if a component fails", or "queue".
- **Key facts:**
  - ==Pull-based (consumers poll)==; each message is processed by one consumer and then deleted.
  - **Standard queues:** nearly unlimited throughput, at-least-once delivery, best-effort ordering.
  - **FIFO queues:** first-in-first-out ordering and exactly-once processing.
  - Messages are retained 4 days by default, configurable up to 14 days.
  - Serverless and fully managed; pay per request.
- **Don't confuse with:** **SNS** (push to many subscribers at once). **Kinesis Data Streams** (real-time streaming where multiple consumers read the same ordered records for analytics). **Amazon MQ** (managed Apache ActiveMQ/RabbitMQ for migrating apps that use standard protocols; not on the in-scope list).
- **Docs:** [What is Amazon SQS?](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)

## AWS Step Functions

> [!summary] Integrate with Lambda functions and view application workflows as a series of event-driven steps.

- **What it does:** Step Functions is a serverless orchestration service. You define a workflow (a "state machine") of steps, such as call a Lambda function, wait for approval, branch on a result, retry on error, and Step Functions runs it and shows its progress visually.
- **Choose it when:** the question says "coordinate multiple Lambda functions", "orchestrate a multi-step workflow", "visual workflow", "state machine", or "built-in retries and error handling across steps".
- **Key facts:**
  - Serverless; workflows are designed visually (Workflow Studio) or in Amazon States Language (JSON).
  - Integrates directly with many AWS services, not only Lambda.
  - **Standard workflows** can run up to one year (long-running, auditable); **Express workflows** are for high-volume, short-duration event processing.
  - Built-in error handling, retries, parallel branches, and human-approval steps.
- **Don't confuse with:** **EventBridge** (routes individual events; does not manage a multi-step sequence with state). **SQS** (queues messages; no workflow logic). **CodePipeline** (orchestrates software release stages, not application business workflows).
- **Docs:** [What is AWS Step Functions?](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
