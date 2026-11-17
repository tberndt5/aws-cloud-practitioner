---
tags:
  - flashcards/services
---
# Flashcards: Services B

Cost Management, Customer Engagement, Developer Tools, End-User Computing, Frontend Web and Mobile, IoT, Machine Learning, Migration and Transfer. Reference notes: [[Services Index]].

## Cost Management

An AWS reseller needs to bill its own customers at custom rates with markups. Which service creates that pro forma bill?::AWS Billing Conductor

What effect does AWS Billing Conductor have on the actual invoice AWS sends?::None. It creates a separate pro forma view; the real AWS bill is unchanged.

A finance team wants an email when monthly spend is forecasted to exceed $5,000. Which service?::AWS Budgets

AWS Budgets can send alerts to which two destinations?::Email and Amazon SNS topics

Which AWS Budgets feature can automatically apply an IAM policy or SCP when a threshold is crossed?::Budget actions

Which billing report contains the most comprehensive, line-item cost and usage data, delivered to an S3 bucket?::AWS Cost and Usage Report

Which three services are typically used to analyze the AWS Cost and Usage Report?::Amazon Athena, Amazon Redshift, Amazon QuickSight

A manager wants graphs of the last year's spending by service and a forecast of next year's costs. Which service?::AWS Cost Explorer

Per the CLF-C02 reference guide, how much history and forecast does AWS Cost Explorer show?::Past 12 months of data and a forecast of the next 12 months

A company wants to buy a third-party firewall appliance and pay for it on its AWS bill. Where does it get it?::AWS Marketplace

Which AWS Marketplace capabilities does the exam guide name?::Cost management, governance, and entitlement

A team wants to estimate the monthly cost of an architecture it has not built yet. Which tool?::AWS Pricing Calculator

AWS Pricing Calculator versus AWS Cost Explorer: which one reports on actual past spend?::AWS Cost Explorer (Pricing Calculator estimates planned workloads)

## Customer Engagement

A new startup wants AWS credits, training, and technical resources. Which program?::AWS Activate for Startups

AWS Activate versus the AWS Free Tier: which one is only for startups?::AWS Activate (the Free Tier applies to every new account)

A company wants to hire an AWS Certified freelancer for a short project and pay through its AWS bill. Which service?::AWS IQ

Who does the work in an AWS IQ engagement?::Third-party AWS Certified freelancers or consulting firms, not AWS employees

An enterprise without cloud operations staff wants AWS to handle patching, monitoring, and incident response on an ongoing basis. Which service?::AWS Managed Services (AMS)

AMS versus AWS Support: which one operates your infrastructure for you?::AWS Managed Services (AMS)

What are the five AWS Support plans tested on CLF-C02?::Basic, Developer, Business, Enterprise On-Ramp, Enterprise

Which support plan has a 15-minute response time for business-critical system down?::Enterprise (Enterprise On-Ramp is 30 minutes)

Which is the lowest support plan with 24/7 phone access and the full set of Trusted Advisor checks?::Business

## Developer Tools

A team wants to turn features on or off in a running app without deploying new code. Which service?::AWS AppConfig

AWS AppConfig is a capability of which larger service?::AWS Systems Manager

An admin wants to script AWS tasks from a terminal on a laptop. Which tool?::AWS CLI

What credentials does the AWS CLI use for programmatic access?::Access keys (access key ID and secret access key) or temporary credentials

A developer wants a full IDE with an editor, debugger, and terminal in the web browser. Which service?::AWS Cloud9

A user wants to run AWS CLI commands from the console with no local install and no credential setup. Which service?::AWS CloudShell

AWS Cloud9 versus AWS CloudShell: which is only a command-line shell?::AWS CloudShell (Cloud9 is a full IDE)

A team needs a managed repository for npm, PyPI, and Maven packages. Which service?::AWS CodeArtifact

Which service compiles source code, runs unit tests, and produces deployable artifacts with no build servers?::AWS CodeBuild

Which service hosts private Git repositories on AWS?::AWS CodeCommit

AWS CodeCommit versus AWS CodeArtifact: which stores source code?::AWS CodeCommit (CodeArtifact stores software packages)

Which service automates application deployments to EC2 instances and on-premises servers?::AWS CodeDeploy

Besides EC2 and on-premises servers, which two compute targets can AWS CodeDeploy deploy to?::AWS Lambda and Amazon ECS

Which service orchestrates the full release process (source, build, test, deploy) for continuous delivery?::AWS CodePipeline

Put these in CI/CD order: CodeDeploy, CodeCommit, CodeBuild.::CodeCommit, then CodeBuild, then CodeDeploy (orchestrated by CodePipeline)

Which service provided project templates and one dashboard to set up a whole development toolchain quickly?::AWS CodeStar

A developer needs to trace requests across microservices to find where latency occurs. Which service?::AWS X-Ray

AWS X-Ray versus AWS CloudTrail: which one records who made an API call?::AWS CloudTrail (X-Ray traces application requests)

A developer wants Python application code to call Amazon S3. What does the developer use?::An AWS SDK (for Python, Boto3)

## End-User Computing

A company wants to stream a single desktop design application to users' browsers without giving them a full desktop. Which service?::Amazon AppStream 2.0

Remote employees each need a persistent virtual Windows desktop with no local hardware to manage. Which service?::Amazon WorkSpaces

Amazon WorkSpaces versus AppStream 2.0: which delivers a full desktop?::Amazon WorkSpaces (AppStream 2.0 streams individual applications)

Employees only need secure browser access to internal websites and SaaS apps, with no data left on their devices. Which service?::Amazon WorkSpaces Web

## Frontend Web and Mobile

A frontend developer wants to add sign-in and data to a React app and host it with Git-based CI/CD. Which service?::AWS Amplify

A mobile app needs a GraphQL API with real-time data updates. Which service?::AWS AppSync

GraphQL API versus REST API on AWS: which services?::GraphQL is AWS AppSync; REST, HTTP, and WebSocket is Amazon API Gateway

A team must test its app on many real Android and iOS phones without buying them. Which service?::AWS Device Farm

## Internet of Things (IoT)

A manufacturer needs to securely connect millions of sensors to AWS and route their messages to other services. Which service?::AWS IoT Core

Which lightweight messaging protocol is most associated with AWS IoT Core?::MQTT

Devices on a remote site must run Lambda functions and ML inference locally and keep working offline. Which service?::AWS IoT Greengrass

AWS IoT Core versus IoT Greengrass: which one runs on the edge device?::AWS IoT Greengrass

## Machine Learning

A retailer wants to analyze customer reviews for positive or negative sentiment. Which service?::Amazon Comprehend

Employees want to ask natural-language questions across internal documents and get precise answers. Which service?::Amazon Kendra

A company wants a chatbot for its website and contact center. Which service?::Amazon Lex

Amazon Lex uses the same technology as which Amazon product?::Amazon Alexa

A news site wants audio versions of its articles. Which service?::Amazon Polly

An app must verify users by comparing a selfie to an ID photo. Which service?::Amazon Rekognition

Data scientists need to build, train, and deploy their own custom ML models. Which service?::Amazon SageMaker

A bank wants to extract fields and tables from scanned loan forms, including handwriting. Which service?::Amazon Textract

Amazon Textract versus Amazon Comprehend: which one pulls text out of a scanned document?::Amazon Textract (Comprehend analyzes the meaning of text)

A call center wants text transcripts of recorded customer calls. Which service?::Amazon Transcribe

Amazon Polly versus Amazon Transcribe: which converts speech to text?::Amazon Transcribe (Polly converts text to speech)

A support portal must show product documentation in Spanish, French, and Japanese. Which service?::Amazon Translate

## Migration and Transfer

Before migrating, a company needs an inventory of on-premises servers, their utilization, and dependencies. Which service?::AWS Application Discovery Service

A company wants to lift and shift (rehost) hundreds of servers to EC2 with minimal downtime. Which service?::AWS Application Migration Service

Which migration strategy (R) does AWS Application Migration Service perform?::Rehost (lift and shift)

A company wants to migrate an Oracle database to AWS while the source stays fully operational. Which service moves the data?::AWS Database Migration Service (AWS DMS)

Which service converts a database schema and stored procedures from Oracle to Amazon Aurora PostgreSQL?::AWS Schema Conversion Tool (AWS SCT)

AWS SCT is required for which type of database migration?::Heterogeneous (different source and target engines); same-engine migrations use DMS alone

Which service gives one dashboard to track the status of every application migration across tools?::AWS Migration Hub

A site with little bandwidth must move 60 TB to Amazon S3. Which service family?::AWS Snow Family (Snowball Edge Storage Optimized)

Which Snow device is a 45-foot shipping container that moves up to 100 PB?::AWS Snowmobile

Which Snow device is the smallest and most portable, with 8 TB (HDD) or 14 TB (SSD) of storage?::AWS Snowcone

Which Snowball Edge option is meant for heavy edge computing such as ML inference in a disconnected location?::Snowball Edge Compute Optimized

Business partners upload files over SFTP; the company wants a managed endpoint that stores them in Amazon S3. Which service?::AWS Transfer Family

Which protocols does AWS Transfer Family support?::SFTP, FTPS, FTP, and AS2
