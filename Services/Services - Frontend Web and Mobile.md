---
tags:
  - clf-c02
  - services
  - services/frontend-web-and-mobile
category: "Frontend Web and Mobile"
status: not-started
---
# Services: Frontend Web and Mobile

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Exam guide 3.8 asks you to identify "the services that can create and deploy frontend and mobile services". The objective is covered in [[3.8 Other In-Scope Service Categories]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#AWS Amplify]] | Tools to build, host, and deploy full-stack web/mobile apps | "Frontend developers", "full-stack web or mobile app", "host a static site with CI/CD" |
| [[#AWS AppSync]] | Managed GraphQL and pub/sub APIs | "GraphQL", "real-time data sync", "combine multiple data sources in one API" |
| [[#AWS Device Farm]] | Test apps on real phones, tablets, and browsers | "Test on many real devices", "Android and iOS testing", "browser testing" |

## AWS Amplify

> [!summary] Set of purpose-built tools and features to build full-stack applications.

- **What it does:** Helps frontend web and mobile developers build and deploy full-stack apps on AWS quickly. It provides libraries and UI components, a backend builder (authentication, data, storage, APIs), and Amplify Hosting with Git-based CI/CD for web apps.
- **Choose it when:** A web or mobile developer with little cloud experience wants to add a backend (sign-in, data, storage) and host the app with minimal AWS setup.
- **Key facts:**
  - Supports popular frameworks such as React, Angular, Vue, Next.js, iOS, Android, and Flutter.
  - ==Amplify Hosting==: deploys and hosts static and server-side-rendered web apps from a Git repository.
  - Uses other services behind the scenes, such as Amazon Cognito for authentication and AWS AppSync for data.
- **Don't confuse with:** [[Services - Compute#AWS Elastic Beanstalk|AWS Elastic Beanstalk]] (deploys server-side web applications on EC2) and [[#AWS AppSync]] (the API layer that Amplify can use).
- **Docs:** [What is AWS Amplify Hosting?](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)

## AWS AppSync

> [!summary] Connect applications and services to data and events with GraphQL and pub/sub APIs.

- **What it does:** A managed service for building GraphQL APIs, which let an app request exactly the data it needs from multiple sources (DynamoDB, Lambda, HTTP endpoints, databases) in one call. It also supports real-time updates through subscriptions and pub/sub (publish/subscribe) APIs.
- **Choose it when:** The question mentions ==GraphQL==, real-time data for web or mobile apps, or offline data synchronization.
- **Key facts:**
  - Fully managed, serverless GraphQL.
  - Real-time subscriptions over WebSockets.
  - Combines data from multiple sources behind one API endpoint.
- **Don't confuse with:** [[Services - Networking and Content Delivery#Amazon API Gateway|Amazon API Gateway]] (REST, HTTP, and WebSocket APIs). GraphQL in a question means AppSync.
- **Docs:** [What is AWS AppSync?](https://docs.aws.amazon.com/appsync/latest/devguide/what-is-appsync.html)

## AWS Device Farm

> [!summary] App testing for Android, iOS, and web apps.

- **What it does:** Lets you test mobile and web applications on real physical phones and tablets, and on desktop browsers, hosted in the AWS Cloud. You can run automated test scripts or interact with a device remotely in real time.
- **Choose it when:** A team must test an app across many device models, operating systems, or browsers without buying the devices.
- **Key facts:**
  - ==Real devices==, not emulators, for Android and iOS.
  - Automated tests or remote access sessions.
  - Results include logs, screenshots, videos, and performance data.
- **Don't confuse with:** [[Services - Developer Tools#AWS CodeBuild|AWS CodeBuild]] (runs unit tests during a build, not on real devices). Load and performance testing of the backend is out of scope for the exam.
- **Docs:** [What is AWS Device Farm?](https://docs.aws.amazon.com/devicefarm/latest/developerguide/welcome.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
