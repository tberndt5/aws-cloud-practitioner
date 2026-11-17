---
tags:
  - clf-c02
  - services
  - services/developer-tools
category: "Developer Tools"
status: not-started
---
# Services: Developer Tools

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Ways to access AWS (console, CLI, SDKs, APIs, infrastructure as code) are taught in [[3.1 Deploying and Operating in the AWS Cloud]]; the developer-tools objective is in [[3.8 Other In-Scope Service Categories]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#AWS AppConfig]] | Deploy app configuration and feature flags safely | "Feature flags", "change app settings without redeploying code" |
| [[#AWS CLI]] | Command-line tool for AWS services | "Command line", "scripts", "terminal" |
| [[#AWS Cloud9]] | Browser-based IDE with built-in terminal | "Cloud IDE", "write and debug code in a browser" |
| [[#AWS CloudShell]] | Pre-authenticated browser shell in the console | "Run CLI from the console", "no local install", "pre-authenticated" |
| [[#AWS CodeArtifact]] | Managed repository for software packages | "npm/Maven/PyPI packages", "artifact repository", "dependencies" |
| [[#AWS CodeBuild]] | Compiles code, runs tests, produces artifacts | "Build", "compile", "run unit tests" |
| [[#AWS CodeCommit]] | Private hosted Git repositories | "Source control", "Git repository", "version control" |
| [[#AWS CodeDeploy]] | Automates deployments to EC2, on-premises, Lambda, ECS | "Deploy", "rolling/blue-green", "on-premises servers" |
| [[#AWS CodePipeline]] | Orchestrates the CI/CD release pipeline | "Continuous delivery", "automate release process", "pipeline" |
| [[#AWS CodeStar]] | Project dashboard tying the Code services together | "Quickly set up a whole dev project/toolchain", "project templates" |
| [[#AWS X-Ray]] | Traces requests through distributed applications | "Trace", "debug microservices", "find bottlenecks", "service map" |
| [[#AWS SDKs]] | Language libraries to call AWS from code | "Programming language", "call AWS APIs from application code" |

> [!tip] The CI/CD chain in order
> **CodeCommit** (store source) → **CodeBuild** (compile and test) → **CodeDeploy** (release to servers) — all orchestrated by **CodePipeline**. **CodeArtifact** holds the packages builds depend on. **CodeStar** wraps the whole chain in a project dashboard. **X-Ray** troubleshoots the running app.

## AWS AppConfig

> [!summary] Create, manage, and quickly deploy application configurations.

- **What it does:** Stores application configuration data and feature flags separately from code and deploys changes to running applications gradually, with validation and automatic rollback. It is a capability of AWS Systems Manager.
- **Choose it when:** A team wants to turn features on or off, or change application settings, without deploying new code, and wants safe, controlled rollout.
- **Key facts:**
  - Supports ==feature flags== and dynamic configuration.
  - Validates configurations before deployment and can roll back automatically if CloudWatch alarms fire.
  - Works with apps on EC2, containers, Lambda, mobile apps, and IoT devices.
  - Part of AWS Systems Manager.
- **Don't confuse with:** [[#AWS CodeDeploy]] (deploys application code, not configuration) and [[Services - Security, Identity, and Compliance#AWS Secrets Manager|AWS Secrets Manager]] (stores and rotates credentials).
- **Docs:** [What is AWS AppConfig?](https://docs.aws.amazon.com/appconfig/latest/userguide/what-is-appconfig.html)

## AWS CLI

> [!summary] Interact with AWS services through commands in the command-line shell.

- **What it does:** A unified, open-source tool you install on Windows, macOS, or Linux to control AWS services from a terminal and automate them through scripts. It calls the same public APIs as the console and SDKs.
- **Choose it when:** The question involves scripting, automation from a terminal, or programmatic access without writing application code.
- **Key facts:**
  - One of the three access methods (console, CLI, SDK); all use AWS APIs underneath.
  - Authenticates with ==access keys== (access key ID and secret access key) or temporary credentials; never use root user access keys.
  - Pre-installed in [[#AWS CloudShell]].
  - Good for repeatable operations, unlike one-off clicks in the console.
- **Don't confuse with:** [[#AWS SDKs]] (libraries used inside application code) and [[#AWS CloudShell]] (a browser shell that already has the CLI installed).
- **Docs:** [What is the AWS CLI?](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)

## AWS Cloud9

> [!summary] An integrated development environment (IDE) with a built-in terminal that supports several programming languages.

- **What it does:** A cloud-based IDE you open in a web browser to write, run, and debug code. The environment runs on an EC2 instance (or your own server over SSH), so nothing needs to be installed locally, and multiple developers can edit together in real time.
- **Choose it when:** The scenario asks for a browser-based code editor or IDE, or real-time pair programming in the cloud.
- **Key facts:**
  - ==Full IDE== (editor, debugger, terminal) in the browser.
  - Runs on an EC2 instance that Cloud9 can create and stop for you, or on your own server via SSH.
  - Supports real-time collaborative editing.
  - Preconfigured with the AWS CLI and SDKs.
- **Don't confuse with:** [[#AWS CloudShell]] (a command-line shell only, no code editor or IDE).
- **Docs:** [What is AWS Cloud9?](https://docs.aws.amazon.com/cloud9/latest/user-guide/welcome.html)

Current status: AWS Cloud9 is no longer available to new customers (since July 25, 2024); existing customers can keep using it, and AWS suggests IDE Toolkits or CloudShell instead.

## AWS CloudShell

> [!summary] A browser-based, pre-authenticated shell that users can launch directly from the console.

- **What it does:** Opens a command-line shell from the AWS Management Console, already signed in with your console credentials. The AWS CLI and common tools are pre-installed, so you can run commands without installing or configuring anything on your machine.
- **Choose it when:** Someone needs to run AWS CLI commands quickly from the browser, without installing the CLI or managing access keys.
- **Key facts:**
  - ==Pre-authenticated== with the console user's credentials.
  - No additional charge; up to 1 GB of persistent home-directory storage per Region.
  - Bash, PowerShell, and Z shell available; AWS CLI v2, Python, Node.js, and git pre-installed.
- **Don't confuse with:** [[#AWS Cloud9]] (full IDE) and the [[#AWS CLI]] installed locally (requires setup and credentials). Systems Manager Session Manager gives a shell on your EC2 instances, not an AWS-API shell.
- **Docs:** [What is AWS CloudShell?](https://docs.aws.amazon.com/cloudshell/latest/userguide/welcome.html)

## AWS CodeArtifact

> [!summary] Artifact repository that helps companies to store and share software packages for application development.

- **What it does:** A fully managed repository for software packages (dependencies) used during builds. It works with common package managers and can fetch and cache packages from public repositories.
- **Choose it when:** A team needs a central, secure place to store, publish, and share code packages and dependencies.
- **Key facts:**
  - Works with npm, pip (PyPI), Maven, Gradle, NuGet, and other package managers.
  - Can proxy and cache public repositories such as npmjs and PyPI.
  - Fully managed; pay for storage and requests.
- **Don't confuse with:** [[#AWS CodeCommit]] (stores source code in Git) and [[Services - Containers#Amazon Elastic Container Registry (Amazon ECR)|Amazon ECR]] (stores container images).
- **Docs:** [What is AWS CodeArtifact?](https://docs.aws.amazon.com/codeartifact/latest/ug/welcome.html)

## AWS CodeBuild

> [!summary] Compiles source code, runs unit tests, and produces artifacts that are ready to deploy.

- **What it does:** A fully managed continuous integration (CI) service. It spins up build environments on demand, runs your build and test commands, and outputs deployable artifacts.
- **Choose it when:** The question says compile, build, or run tests automatically without managing build servers.
- **Key facts:**
  - ==No build servers to manage==; scales automatically and runs builds in parallel.
  - Pay per minute of build time.
  - Commonly the build stage in [[#AWS CodePipeline]].
- **Don't confuse with:** [[#AWS CodeDeploy]] (deploys the built artifact) and [[#AWS CodePipeline]] (orchestrates the stages).
- **Docs:** [What is AWS CodeBuild?](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)

## AWS CodeCommit

> [!summary] Host private Git repositories, store and manage assets.

- **What it does:** A fully managed source control service that hosts private Git repositories. It works with standard Git tools and supports pull requests, branches, and code reviews.
- **Choose it when:** A team needs private, managed Git-based version control on AWS.
- **Key facts:**
  - ==Git-based==; encrypted at rest and in transit; integrated with IAM.
  - No repository size limit and no servers to manage.
  - Commonly the source stage of [[#AWS CodePipeline]].
- **Don't confuse with:** [[#AWS CodeArtifact]] (packages, not source code) and S3 versioning (file versions, not collaborative code development).
- **Docs:** [What is AWS CodeCommit?](https://docs.aws.amazon.com/codecommit/latest/userguide/welcome.html)

Current status: CodeCommit was closed to new customers on July 25, 2024, then reopened to new customers on November 25, 2025 (CodeCommit document history).

## AWS CodeDeploy

> [!summary] Automate application deployments to on-premises instances or select AWS resources.

- **What it does:** Automates deploying new application versions to Amazon EC2 instances, on-premises servers, AWS Lambda functions, and Amazon ECS services. It supports in-place and blue/green deployments and can roll back on failure.
- **Choose it when:** The scenario needs automated, repeatable deployments, especially to ==on-premises servers== as well as EC2.
- **Key facts:**
  - Targets: EC2, on-premises servers, Lambda, ECS.
  - Deployment styles: in-place (rolling) and blue/green; automatic rollback.
  - Free for EC2 and Lambda deployments; charged per on-premises instance update.
- **Don't confuse with:** [[Services - Compute#AWS Elastic Beanstalk|AWS Elastic Beanstalk]] (provisions and manages the whole environment for you) and [[Services - Management and Governance#AWS CloudFormation|AWS CloudFormation]] (provisions infrastructure, not app releases).
- **Docs:** [What is CodeDeploy?](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)

## AWS CodePipeline

> [!summary] Model, visualize, and automate the steps to release software with continuous delivery.

- **What it does:** A continuous delivery service that runs a release pipeline every time code changes: source, build, test, and deploy stages. It connects AWS tools (CodeCommit, CodeBuild, CodeDeploy) and third-party tools such as GitHub and Jenkins.
- **Choose it when:** The question asks to automate the whole release process end to end, or mentions CI/CD orchestration.
- **Key facts:**
  - ==Orchestrator== of CI/CD; it calls other services to do the work.
  - Stages and actions are visualized in the console.
  - Integrates with third-party tools as well as AWS services.
- **Don't confuse with:** [[#AWS CodeBuild]] and [[#AWS CodeDeploy]] (individual stages) and [[Services - Application Integration#AWS Step Functions|AWS Step Functions]] (application workflow orchestration, not software release).
- **Docs:** [What is AWS CodePipeline?](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)

## AWS CodeStar

> [!summary] Create and manage software development projects by integrating AWS services in the project development toolchain.

- **What it does:** Provided project templates and a unified dashboard that set up a complete toolchain (CodeCommit, CodeBuild, CodeDeploy, CodePipeline) for a new project in minutes, with team access management and issue tracking integration.
- **Choose it when:** The scenario wants to quickly start a new development project with the full CI/CD toolchain already wired together.
- **Key facts:**
  - Templates for common app types and languages.
  - ==Single dashboard== across the Code services; manages team roles (owner, contributor, viewer).
  - No additional charge; you pay for the underlying resources.
- **Don't confuse with:** [[#AWS CodePipeline]] (one pipeline, not a whole project with dashboard and team access).
- **Docs:** [AWS CodeStar documentation](https://aws.amazon.com/documentation-overview/codestar/)

Current status: AWS CodeStar is fully shut down; end of support was July 25, 2024 (AWS General Reference, "Services in Full Shutdown"). AWS CodeStar Connections is a separate feature, renamed AWS CodeConnections.

## AWS X-Ray

> [!summary] Collects data about application requests and provides tools to view, filter, and gain insights into the data.

- **What it does:** Traces requests as they travel through a distributed application (for example microservices or Lambda functions) and builds a service map showing latency and errors at each step.
- **Choose it when:** The question asks to debug, trace, or find performance bottlenecks in a microservices or serverless application.
- **Key facts:**
  - ==Distributed tracing== and a visual service map.
  - Identifies latency, errors, and faults per component.
  - Works with EC2, ECS, Lambda, Elastic Beanstalk, API Gateway.
- **Don't confuse with:** [[Services - Management and Governance#Amazon CloudWatch|Amazon CloudWatch]] (metrics, logs, alarms) and [[Services - Management and Governance#AWS CloudTrail|AWS CloudTrail]] (records who made which API call, for auditing).
- **Docs:** [What is AWS X-Ray?](https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html)

## AWS SDKs

> [!summary] Use software development kits to develop applications in your preferred programming language.

- **What it does:** Language-specific libraries (for example Python/Boto3, Java, JavaScript, .NET, Go) that let application code call AWS services. They handle authentication, retries, and request signing.
- **Choose it when:** A developer wants application code in a particular programming language to interact with AWS services.
- **Key facts:**
  - One of the programmatic access methods in exam guide 3.1 (APIs, SDKs, CLI).
  - Use the same credentials and APIs as the CLI.
  - Listed in the exam guide appendix.
- **Don't confuse with:** [[#AWS CLI]] (commands in a terminal) and [[Services - Management and Governance#AWS CloudFormation|AWS CloudFormation]] (declarative templates for infrastructure as code).
- **Docs:** [Tools to build on AWS](https://aws.amazon.com/developer/tools/)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
