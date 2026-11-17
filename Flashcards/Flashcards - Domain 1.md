---
tags:
  - flashcards/domain-1
---
# Flashcards - Domain 1: Cloud Concepts

Review notes: [[1.1 Benefits of the AWS Cloud]] · [[1.2 Design Principles - Well-Architected Framework]] · [[1.3 Migration Strategies and AWS CAF]] · [[1.4 Cloud Economics]]

## 1.1 Benefits of the AWS Cloud

What are the six advantages of cloud computing in AWS wording::Trade fixed expense for variable expense; benefit from massive economies of scale; stop guessing capacity; increase speed and agility; stop spending money running and maintaining data centers; go global in minutes

Which advantage of cloud computing describes paying only when you consume resources instead of investing in data centers up front::Trade fixed expense for variable expense

Which advantage of cloud computing explains why AWS can charge lower prices because it aggregates usage from hundreds of thousands of customers::Benefit from massive economies of scale

Which advantage of cloud computing removes the need to forecast infrastructure needs before deploying an application::Stop guessing capacity

Which advantage of cloud computing describes reducing the time to provision resources from weeks to minutes::Increase speed and agility

Which advantage of cloud computing lets a company focus on its customers instead of racking, stacking, and powering servers::Stop spending money running and maintaining data centers

Which advantage of cloud computing describes deploying an application in multiple Regions with a few clicks for lower latency::Go global in minutes

What does "economies of scale" mean in cloud terms::AWS's huge aggregated usage lowers its cost per unit, which it passes on as lower pay-as-you-go prices

What is high availability::A system stays operational with minimal downtime, usually by running across multiple Availability Zones

What is fault tolerance::A system keeps running with no interruption when a component fails, because redundant components take over

What is elasticity::Automatically adding and removing resources to match demand, so you pay only for what you need

What is scalability::The ability to grow capacity to handle increased load, vertically or horizontally

What is the difference between vertical and horizontal scaling::Vertical makes one resource bigger (scale up); horizontal adds more resources (scale out)

What is agility in cloud terms::The speed with which an organization can provision resources, experiment, and deliver new features

A team can spin up a test environment in minutes and delete it after an experiment. Which benefit is this::Agility (increase speed and agility)

## 1.2 Well-Architected Framework

What are the six pillars of the AWS Well-Architected Framework::Operational excellence; security; reliability; performance efficiency; cost optimization; sustainability

Which pillar is defined as running systems to deliver business value at the lowest price point::Cost optimization

Which pillar is defined as a workload performing its intended function correctly and consistently when expected::Reliability

Which pillar is defined as using computing resources efficiently to meet requirements as demand changes and technologies evolve::Performance efficiency

Which pillar focuses on energy consumption and environmental impact::Sustainability

Which pillar focuses on running and monitoring workloads and continuously improving processes and procedures::Operational excellence

Which pillar includes "automatically recover from failure" and "test recovery procedures"::Reliability

Which pillar includes "perform operations as code" and "make frequent, small, reversible changes"::Operational excellence

Which pillar includes "implement a strong identity foundation" and "apply security at all layers"::Security

Which pillar includes "democratize advanced technologies" and "use serverless architectures"::Performance efficiency

Which pillar includes "adopt a consumption model" and "analyze and attribute expenditure"::Cost optimization

Which pillar includes "maximize utilization" and "reduce the downstream impact of your cloud workloads"::Sustainability

Which pillar includes "go global in minutes" as a design principle::Performance efficiency

Name three general design principles of the Well-Architected Framework::Any of: stop guessing capacity needs; test systems at production scale; automate with architectural experimentation in mind; consider evolutionary architectures; drive architectures using data; improve through game days

Which AWS service reviews a workload against Well-Architected best practices by asking questions per pillar::AWS Well-Architected Tool

What does the AWS Well-Architected Tool produce after a review::High- and medium-risk issues and an improvement plan (with milestones to track progress)

Well-Architected Tool or Trusted Advisor: which one runs automated checks against resources in your account::AWS Trusted Advisor

## 1.3 Migration and AWS CAF

What are the six AWS CAF perspectives::Business, People, Governance, Platform, Security, Operations

What are the four AWS CAF business outcomes named in the exam guide::Reduced business risk; improved ESG performance; increased revenue; increased operational efficiency

What are the four AWS CAF transformation phases in order::Envision, Align, Launch, Scale

Which CAF phase identifies capability gaps across the six perspectives::Align

Which CAF phase delivers pilot initiatives in production::Launch

Which CAF perspective includes cloud fluency, workforce transformation, and culture evolution::People

Which CAF perspective includes cloud financial management, risk management, and benefits management::Governance

Which CAF perspective includes strategy management, portfolio management, and data monetization::Business

Which CAF perspective includes platform architecture, platform engineering, and CI/CD::Platform

Which CAF perspective includes observability, patch management, and incident and problem management::Operations

Which CAF perspective includes threat detection, vulnerability management, and data protection::Security

Which CAF perspective's common stakeholders are the CEO, CFO, COO, CIO, and CTO::Business

Which CAF perspective's common stakeholders include the CISO and chief compliance officer::Security

What are the 7 Rs of migration::Retire, Retain, Rehost, Relocate, Repurchase, Replatform, Refactor (re-architect)

Which migration strategy is called "lift and shift"::Rehost

Which migration strategy is called "lift, tinker, and shift"::Replatform

Which migration strategy is called "drop and shop"::Repurchase

Which migration strategy redesigns an application to use cloud-native features::Refactor (re-architect)

Which migration strategy moves VMware workloads to VMware Cloud on AWS without changes::Relocate

Moving a self-managed SQL Server database to Amazon RDS for SQL Server is which strategy::Replatform

Replacing an on-premises CRM with a SaaS CRM is which strategy::Repurchase

Which tool migrates a database while the source stays operational and supports ongoing replication::AWS Database Migration Service (AWS DMS)

What do you add to AWS DMS when migrating between different database engines::AWS Schema Conversion Tool (AWS SCT)

When does AWS Snow Family fit a migration::Large data volumes with limited, slow, or no network connectivity

Which Snow Family option moves up to 100 PB in a shipping container::AWS Snowmobile

## 1.4 Cloud Economics

What is CapEx::Capital expenditure; up-front spending on physical assets such as servers and data centers

What is OpEx::Operational expenditure; ongoing spending for services and operations, such as a monthly AWS bill

What is the difference between fixed and variable costs::Fixed costs stay the same regardless of usage; variable costs rise and fall with usage

Moving to AWS shifts IT spending from which type of expense to which::From fixed (capital) expense to variable (operational) expense

What is total cost of ownership (TCO)::The full lifetime cost of a solution, including hardware, software, facilities, power, cooling, labor, and maintenance

Name four on-premises costs that moving to AWS removes or reduces::Any four of: hardware purchase and refresh; data center space; power and cooling; physical security; maintenance labor; idle over-provisioned capacity

What is rightsizing::Matching instance types and sizes to actual workload needs at the lowest cost

Should you rightsize before or after buying Reserved Instances or Savings Plans::Before, so you do not commit to the wrong size

Which AWS service uses machine learning to recommend optimal instance types (rightsizing)::AWS Compute Optimizer

What does BYOL mean::Bring Your Own License; reuse software licenses you already own on AWS and pay only for infrastructure

What does "license included" mean::The software license cost is built into the AWS price, and you pay as you go

Which EC2 option is often required for BYOL licensed per physical socket or core::Dedicated Hosts

Which AWS service centrally tracks and enforces software license usage across AWS and on premises::AWS License Manager

What is infrastructure as code (IaC)::Defining and provisioning infrastructure from text templates instead of manual steps

Name three benefits of automating provisioning with AWS CloudFormation::Repeatable and consistent environments; fewer human errors; faster deployment; version control; easy teardown and rollback

What is a managed service::A service where AWS operates the underlying infrastructure and handles tasks such as patching, backups, and scaling

Name the four managed services the exam guide uses as examples::Amazon RDS, Amazon ECS, Amazon EKS, Amazon DynamoDB

With Amazon RDS, who patches the database engine and underlying OS::AWS

With Amazon EKS, which part of Kubernetes does AWS manage::The Kubernetes control plane