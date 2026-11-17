---
tags:
  - clf-c02
  - cheat-sheet
---
# Security Services at a Glance

## Detect and investigate

| Service | One job | Cue words |
| --- | --- | --- |
| GuardDuty | Threat detection from logs (CloudTrail, VPC Flow Logs, DNS) | malicious, compromised, crypto mining, unusual activity |
| Inspector | Vulnerability scanning of EC2, ECR images, Lambda | CVE, unpatched software, network exposure |
| Macie | Sensitive data discovery in S3 | PII, credit card numbers, sensitive data in buckets |
| Detective | Root-cause investigation | investigate, root cause, behavior graph |
| Security Hub | Aggregate and prioritize findings, posture checks | single dashboard, across accounts, CIS benchmark |
| Trusted Advisor | Best-practice checks (cost, security, performance, fault tolerance, limits, ops) | open ports, root MFA, public snapshots |

Mnemonic: **GuardDuty guards, Inspector inspects, Macie finds PII, Detective finds root cause, Hub collects.**

## Protect the network and apps

| Service | Protects against | Scope |
| --- | --- | --- |
| Shield Standard | Common Layer 3/4 DDoS | Free, automatic, everyone |
| Shield Advanced | Large and Layer 7 DDoS; SRT 24/7 (needs Business or Enterprise Support); cost protection | Paid ($3,000/month, 1-year); EIP, ELB, CloudFront, Global Accelerator, Route 53 |
| WAF | SQL injection, XSS, bad bots, IP/country blocks, rate limits (HTTP/S, Layer 7) | CloudFront, ALB, API Gateway, AppSync, Cognito |
| Firewall Manager | Inconsistent rules across accounts | Org-wide WAF, Shield Advanced, SGs, Network Firewall; needs Organizations |
| Network Firewall | Unwanted VPC traffic; IDS/IPS | VPC perimeter |
| Security group | Instance firewall | Stateful, allow only |
| Network ACL | Subnet firewall | Stateless, allow and deny, numbered rules |

## Data protection

| Service | Use |
| --- | --- |
| KMS | Managed encryption keys, at rest, integrated with most services |
| CloudHSM | Dedicated single-tenant HSM, you control keys |
| ACM | Free public SSL/TLS certs for integrated services, auto-renew (in transit) |
| Secrets Manager | Store and **auto-rotate** secrets |
| SSM Parameter Store | Config values and secrets, free standard tier, no built-in rotation |

## Audit, monitor, comply

| Service | Answers |
| --- | --- |
| CloudTrail | **Who** did what API call, when (90-day event history; trail to S3 for longer) |
| CloudWatch | **How** is it performing: metrics, logs, alarms |
| Config | **What** did it look like, what changed, is it compliant with rules |
| Audit Manager | Evidence collection for **your** audits (PCI, HIPAA, GDPR frameworks) |
| Artifact | **AWS's** audit reports (SOC, ISO, PCI) and agreements (BAA) |

## If the question says X, answer Y

- "Who deleted the resource" → CloudTrail
- "Configuration history" / "resource drifted from rule" → Config
- "Alarm on CPU" → CloudWatch
- "Download SOC 2 / PCI report" → Artifact
- "PII in S3" → Macie
- "Vulnerabilities on EC2" → Inspector
- "Instance talking to a known bad IP" → GuardDuty
- "Root cause of a finding" → Detective
- "One place for all findings" → Security Hub
- "DDoS" → Shield (free = Standard; response team or cost protection = Advanced)
- "SQL injection" / "block a country" → WAF
- "Same firewall rules in every account" → Firewall Manager
- "Rotate database password automatically" → Secrets Manager
- "Dedicated HSM" → CloudHSM
- "HTTPS certificate" → ACM
- "Third-party security tool" → AWS Marketplace

Details: [[2.2 Security, Governance, and Compliance Concepts]] · [[2.4 Security Components and Resources]] · [[Services - Security, Identity, and Compliance]]
