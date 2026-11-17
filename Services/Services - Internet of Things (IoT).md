---
tags:
  - clf-c02
  - services
  - services/internet-of-things-iot
category: "Internet of Things (IoT)"
status: not-started
---
# Services: Internet of Things (IoT)

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Exam guide 3.8 asks you to identify "the services that manage IoT devices". The objective is covered in [[3.8 Other In-Scope Service Categories]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#AWS IoT Core]] | Cloud hub connecting IoT devices to AWS | "Connect billions of devices", "MQTT", "route device messages to AWS services" |
| [[#AWS IoT Greengrass]] | Runs AWS logic locally on edge devices | "Process data locally", "intermittent connectivity", "edge runtime", "run Lambda on devices" |

> [!tip] Cloud or edge?
> Devices send messages **to the cloud**: IoT Core. Code runs **on the device or a local gateway**, even offline: IoT Greengrass.

## AWS IoT Core

> [!summary] Connect and process messages between IoT devices and IoT services.

- **What it does:** A managed cloud service that lets internet-connected devices (sensors, appliances, vehicles) connect securely to AWS and to each other. A message broker receives device messages, and a rules engine routes them to services such as Lambda, DynamoDB, S3, and Kinesis.
- **Choose it when:** A company needs to connect many devices to the cloud, collect their telemetry, and send it to other AWS services for processing or storage.
- **Key facts:**
  - Supports ==MQTT==, HTTPS, MQTT over WebSockets, and LoRaWAN.
  - Mutual authentication and encryption for device connections (X.509 certificates).
  - Device shadows keep a cloud copy of each device's state, even when it is offline.
  - Rules engine filters and routes messages to AWS services.
- **Don't confuse with:** [[#AWS IoT Greengrass]] (runs on the device at the edge). [[Services - Analytics#Amazon Kinesis|Amazon Kinesis]] streams any data in real time but does not manage device identity or connections.
- **Docs:** [What is AWS IoT?](https://docs.aws.amazon.com/iot/latest/developerguide/what-is-aws-iot.html)

## AWS IoT Greengrass

> [!summary] Build, deploy, and manage IoT edge runtime applications on devices.

- **What it does:** Open-source edge runtime and cloud service that lets devices run code (including Lambda functions, containers, and ML inference) locally. Devices can act on data near where it is generated, keep working when disconnected, and sync with the cloud when connectivity returns.
- **Choose it when:** Devices must process data locally for low latency, keep operating with intermittent or no internet connectivity, or reduce the data sent to the cloud.
- **Key facts:**
  - ==Edge computing== for IoT devices and gateways.
  - Runs Lambda functions, Docker containers, and ML models on the device.
  - Works offline and synchronizes with AWS IoT Core when reconnected.
  - Deploy and manage software on fleets of devices from the cloud.
- **Don't confuse with:** [[#AWS IoT Core]] (cloud-side connectivity), [[Services - Compute#AWS Outposts|AWS Outposts]] (AWS racks in your data center), and [[Services - Migration and Transfer#AWS Snow Family|AWS Snow Family]] (rugged devices for edge compute and data transfer).
- **Docs:** [What is AWS IoT Greengrass?](https://docs.aws.amazon.com/greengrass/v2/developerguide/what-is-iot-greengrass.html)

Current status: AWS IoT Greengrass V1 reached full shutdown on October 7, 2026; Greengrass V2 is the current version.

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
