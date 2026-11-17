---
tags:
  - clf-c02
  - services
  - services/analytics
category: "Analytics"
status: not-started
---
# Services: Analytics

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Concepts (data lakes, ETL, streaming versus batch, BI) are taught in [[3.7 AI-ML and Analytics Services]]. This note is the per-service reference. The exam mostly asks you to match a verb in the question (query, stream, transform, visualize, search, warehouse) to one service.

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#Amazon Athena\|Amazon Athena]] | Serverless SQL queries directly on S3 data | "query data in S3 with SQL", "no infrastructure", "ad hoc" |
| [[#AWS Data Exchange\|AWS Data Exchange]] | Marketplace for subscribing to third-party data sets | "find and subscribe to third-party data" |
| [[#Amazon EMR\|Amazon EMR]] | Managed Hadoop and Spark big data clusters | "Hadoop", "Spark", "big data framework", "petabytes of processing" |
| [[#AWS Glue\|AWS Glue]] | Serverless ETL and data catalog | "extract, transform, load", "data catalog", "prepare and integrate data" |
| [[#Amazon Kinesis\|Amazon Kinesis]] | Real-time collection and processing of streaming data | "real time", "near real time", "clickstream", "video streams" |
| [[#Amazon Managed Streaming for Apache Kafka (Amazon MSK)\|Amazon MSK]] | Fully managed Apache Kafka | "Apache Kafka" |
| [[#Amazon OpenSearch Service\|Amazon OpenSearch Service]] | Managed OpenSearch for search and log analytics | "search", "log analytics", "Elasticsearch", "OpenSearch" |
| [[#Amazon QuickSight\|Amazon QuickSight]] | Business intelligence dashboards and visualizations | "dashboards", "business intelligence", "visualize" |
| [[#Amazon Redshift\|Amazon Redshift]] | Petabyte-scale columnar data warehouse | "data warehouse", "OLAP", "complex analytic queries on structured data" |

> [!tip] One-line memory chain
> Ingest with **Kinesis/MSK** → catalog and transform with **Glue** → store in **S3** (data lake) or **Redshift** (warehouse) → query with **Athena** (on S3) or Redshift → visualize with **QuickSight**. **EMR** is the do-it-with-Hadoop/Spark alternative; **OpenSearch** is for search and logs; **Data Exchange** brings in outside data.

## Amazon Athena

> [!summary] Analyze data directly in Amazon S3 by using standard SQL.

- **What it does:** Athena is an interactive, serverless query service. You point it at data already in S3 (CSV, JSON, Parquet, ORC and other formats), define a table schema (often from the AWS Glue Data Catalog), and run standard SQL. There are no servers or clusters to manage.
- **Choose it when:** the question says "query data in S3 with SQL", "ad hoc analysis of logs in S3" (for example CloudTrail or VPC Flow Logs), or "without loading the data into a database".
- **Key facts:**
  - Serverless; ==you pay per query, based on the amount of data scanned==. Compressing and using columnar formats (Parquet) lowers cost.
  - Data stays in S3; nothing is loaded or moved.
  - Uses the AWS Glue Data Catalog to store table definitions.
  - Results can be visualized in Amazon QuickSight.
- **Don't confuse with:** **Redshift** (a provisioned or serverless data warehouse you load data into for repeated complex queries; Athena queries files in place). **S3 Select** (retrieves a subset of one object; not a full query service). **Glue** (prepares and catalogs data; does not answer SQL queries itself).
- **Docs:** [What is Amazon Athena?](https://docs.aws.amazon.com/athena/latest/ug/what-is.html)

## AWS Data Exchange

> [!summary] Find, subscribe to, and use third-party data in the cloud.

- **What it does:** A catalog of data products (files, APIs, Amazon Redshift data shares) published by third-party providers such as financial, weather, or healthcare data companies. Subscribers find a data set, subscribe, and receive it directly in their AWS account, usually into S3.
- **Choose it when:** a company wants to "acquire third-party data", "subscribe to commercial data sets", or "license data from a provider" for analytics or ML.
- **Key facts:**
  - Providers publish; subscribers subscribe; billing goes through AWS (similar model to AWS Marketplace, but for data).
  - Subscribed data lands in your account so you can analyze it with Athena, Redshift, SageMaker, and others.
  - Some data sets are free; many are paid.
- **Don't confuse with:** **AWS Marketplace** (third-party software and services, not mainly data sets). **AWS Glue** (moves and transforms your own data). **AWS DataSync / Transfer Family** (move your own files).
- **Docs:** [What is AWS Data Exchange?](https://docs.aws.amazon.com/data-exchange/latest/userguide/what-is.html)

## Amazon EMR

> [!summary] Run big data frameworks, such as Apache Hadoop and Apache Spark, to process and analyze vast amounts of data.

- **What it does:** EMR (formerly Elastic MapReduce) creates managed clusters of EC2 instances preinstalled with open-source big data tools such as Hadoop, Spark, Hive, Presto, and HBase. AWS handles provisioning and configuration; you run your processing jobs.
- **Choose it when:** the question names Hadoop, Spark, Hive, or "big data processing" on large data sets, or a company wants to move an on-premises Hadoop cluster to AWS.
- **Key facts:**
  - Managed cluster platform; can run on EC2 (and also on EKS or as EMR Serverless).
  - Clusters can be scaled up and down and use Spot Instances to cut cost.
  - Commonly reads from and writes to S3.
  - Use cases: log analysis, ETL at scale, ML data preparation, financial and scientific simulation.
- **Don't confuse with:** **Glue** (serverless ETL, no clusters to size; EMR gives you control of a cluster and the open-source frameworks). **Redshift** (SQL data warehouse). **AWS Batch** (generic batch jobs, not Hadoop/Spark).
- **Docs:** [What is Amazon EMR?](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html)

## AWS Glue

> [!summary] Discover, prepare, move, and integrate data from multiple sources.

- **What it does:** Glue is a serverless data integration service. Crawlers scan data sources and record their schema in the **AWS Glue Data Catalog**; Glue jobs then extract, transform, and load (ETL) the data into targets such as S3 or Redshift.
- **Choose it when:** the question says "ETL", "extract, transform, and load", "prepare data for analytics", "discover and catalog data", or "central metadata repository".
- **Key facts:**
  - Serverless: no infrastructure to manage; pay for the resources jobs use while running.
  - The Glue Data Catalog is the metadata store that Athena, Redshift Spectrum, and EMR can use.
  - Crawlers infer schemas automatically.
  - AWS Glue DataBrew is a visual, no-code data preparation tool within the Glue family.
- **Don't confuse with:** **EMR** (cluster-based Hadoop/Spark). **AWS DMS** (migrates databases; Glue transforms data for analytics). **Athena** (queries data; Glue prepares and catalogs it).
- **Docs:** [What is AWS Glue?](https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html)

## Amazon Kinesis

> [!summary] Collect, process, and analyze video streams and data streams in near real time.

- **What it does:** Kinesis is a family of services for streaming data, meaning records that arrive continuously (clickstreams, IoT telemetry, application logs, video). It ingests the data and makes it available to process within seconds, instead of waiting for a nightly batch.
- **Choose it when:** the question says "real time", "near real time", "streaming", "clickstream", "telemetry", or "ingest video from cameras".
- **Key facts:**
  - **Kinesis Data Streams:** capture and store streams for custom real-time processing by your applications.
  - **Kinesis Data Firehose:** load streaming data into destinations such as S3, Redshift, and OpenSearch with no code to manage.
  - **Kinesis Data Analytics:** analyze streams in real time with SQL or Apache Flink.
  - **Kinesis Video Streams:** ingest and store video streams for analytics and ML.
  - Current status: Kinesis Data Firehose was renamed **Amazon Data Firehose** (February 2024) and Kinesis Data Analytics is now **Amazon Managed Service for Apache Flink** (2023). Exam questions may use either name.
- **Don't confuse with:** **Amazon MSK** (managed Apache Kafka, used when the question names Kafka). **SQS** (message queue for decoupling apps, not a real-time analytics stream). **Glue/EMR** (batch processing).
- **Docs:** [Amazon Kinesis](https://aws.amazon.com/kinesis/)

## Amazon Managed Streaming for Apache Kafka (Amazon MSK)

> [!summary] Build and run applications that use Apache Kafka to process streaming data.

- **What it does:** MSK runs Apache Kafka clusters for you. Apache Kafka is a popular open-source platform for streaming data. AWS provisions, patches, and recovers the Kafka brokers so you can keep using standard Kafka tools and code.
- **Choose it when:** the question specifically mentions **Apache Kafka**, or a company wants to migrate an existing self-managed Kafka workload without changing code.
- **Key facts:**
  - Fully managed and compatible with open-source Kafka APIs.
  - Available as provisioned clusters or MSK Serverless.
  - Data replicated across multiple Availability Zones for high availability.
- **Don't confuse with:** **Kinesis Data Streams** (AWS-native streaming service with its own API; the answer when Kafka is not mentioned). **SQS/SNS** (messaging between application components).
- **Docs:** [What is Amazon MSK?](https://docs.aws.amazon.com/msk/latest/developerguide/what-is-msk.html)

## Amazon OpenSearch Service

> [!summary] Deploy, operate, and scale OpenSearch clusters in the cloud.

- **What it does:** A managed service for OpenSearch, an open-source search and analytics engine (a fork of Elasticsearch). It indexes data so you can run full-text search, log analytics, and real-time application monitoring, and visualize results with OpenSearch Dashboards.
- **Choose it when:** the question says "full-text search", "search engine for a website", "log analytics", "Elasticsearch", or "operational analytics on log data".
- **Key facts:**
  - Successor to Amazon Elasticsearch Service (renamed in 2021); still supports legacy Elasticsearch versions.
  - Includes OpenSearch Dashboards for visualization; an OpenSearch Serverless option exists.
  - Common pipeline: Kinesis Data Firehose loads logs into OpenSearch.
- **Don't confuse with:** **Amazon Kendra** (ML-powered intelligent enterprise search over documents with natural-language questions). **Athena** (SQL on S3). **CloudWatch Logs** (operational logging for AWS resources).
- **Docs:** [What is Amazon OpenSearch Service?](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/what-is.html)

## Amazon QuickSight

> [!summary] Business intelligence service that provides insights in a single data dashboard.

- **What it does:** QuickSight is a serverless, cloud-scale business intelligence (BI) service. You connect it to data sources (S3, Athena, Redshift, RDS, on-premises databases, SaaS apps) and build interactive dashboards, charts, and reports to share with users.
- **Choose it when:** the question says "dashboards", "visualizations", "business intelligence", "share reports with business users", or "ask questions of data in natural language".
- **Key facts:**
  - Serverless and scales to many users; pay-per-session pricing is available for readers.
  - **SPICE** is its in-memory calculation engine for fast dashboards.
  - Includes ML-powered insights and natural-language querying (QuickSight Q).
  - Dashboards can be embedded in applications.
  - Current status: AWS has rebranded the broader product (Amazon Quick Suite, now AWS Quick); the BI capability continues as **Quick Sight**, and existing QuickSight APIs keep working. The exam uses "Amazon QuickSight".
- **Don't confuse with:** **CloudWatch dashboards** (operational metrics of AWS resources, not business BI). **AWS Cost Explorer** (visualizes AWS spend only). **Athena** (queries data; QuickSight visualizes it).
- **Docs:** [What is AWS Quick? (QuickSight user guide)](https://docs.aws.amazon.com/quick/latest/userguide/what-is.html)

## Amazon Redshift

> [!summary] Petabyte-scale data warehouse with automatically provisioned resources and intelligent scaling. (Reference guide lists Redshift under Database; the exam guide lists it under Analytics.)

- **What it does:** Redshift is a fully managed data warehouse: a database optimized for analytics (OLAP, online analytical processing) over large amounts of structured historical data. It stores data in columns and spreads queries across many nodes, so complex SQL queries over billions of rows return quickly.
- **Choose it when:** the question says "data warehouse", "business intelligence over historical data", "complex analytic queries", "OLAP", or "petabyte-scale SQL analytics".
- **Key facts:**
  - Columnar storage and massively parallel processing; uses standard SQL.
  - ==Data warehouse (analytics, OLAP), not a transactional (OLTP) database==; for transactions choose RDS or Aurora.
  - **Redshift Spectrum** queries data in S3 without loading it into Redshift.
  - **Redshift Serverless** removes cluster management.
  - Often fed by Glue or Kinesis Data Firehose and visualized with QuickSight.
- **Don't confuse with:** **RDS/Aurora** (relational OLTP databases for applications). **Athena** (serverless SQL on S3, pay per query, no warehouse). **DynamoDB** (NoSQL key-value).
- **Docs:** [What is Amazon Redshift?](https://docs.aws.amazon.com/redshift/latest/mgmt/welcome.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
