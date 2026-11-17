---
tags:
  - clf-c02
  - cheat-sheet
---
# Well-Architected and CAF

Two frameworks, both with six parts. **Well-Architected = 6 pillars for a workload.** **CAF = 6 perspectives for an organization.** "Pillar" in the question means Well-Architected; "perspective" means CAF.

## Well-Architected Framework: six pillars (mnemonic CROPS + S)

| Pillar | One-liner | Key design principles | Scenario cues |
| --- | --- | --- | --- |
| **Operational excellence** | Run and monitor workloads, continuously improve processes | Perform operations as code (now "safely automate where possible"); frequent, small, reversible changes; refine procedures frequently; anticipate failure; learn from all operational events | Runbooks, deployments, observability, game days, post-incident reviews |
| **Security** | Protect data, systems, assets | Strong identity foundation; maintain (enable) traceability; security at all layers; automate security; protect data in transit and at rest; keep people away from data; prepare for security events | Least privilege, encryption, audit logs, incident response |
| **Reliability** | Perform intended function correctly and consistently; recover | Automatically recover from failure; test recovery procedures; scale horizontally; stop guessing capacity; manage change through automation | Multi-AZ, backups, DR, failover, service quotas |
| **Performance efficiency** | Use resources efficiently as demand and technology change | Democratize advanced technologies; go global in minutes; use serverless; experiment more often; mechanical sympathy | Right instance family, latency, caching, CloudFront |
| **Cost optimization** | Deliver business value at the lowest price point | Cloud financial management; adopt a consumption model; measure overall efficiency; stop spending on undifferentiated heavy lifting; analyze and attribute expenditure | Rightsizing, RIs/Savings Plans/Spot, idle resources, tagging |
| **Sustainability** | Minimize environmental impact, energy use | Understand your impact; set goals; maximize utilization; adopt efficient hardware/software; use managed services; reduce downstream impact | Carbon, energy, utilization, Graviton |

**General design principles:** stop guessing capacity; test at production scale; automate with experimentation in mind; consider evolutionary architectures; drive architectures using data; improve through game days.

**AWS Well-Architected Tool:** free console service; answer questions per pillar for a workload; get high/medium risk issues, an improvement plan, milestones, and lenses. It does not scan your account (that is **Trusted Advisor**).

## AWS CAF: six perspectives (mnemonic "Big People Govern; Platforms Secure Operations")

| Perspective | Owners | Capabilities to recognize |
| --- | --- | --- |
| **Business** | CEO, CFO, COO, CIO, CTO | Strategy, portfolio, innovation, product management; strategic partnership; data monetization; business insights; data science |
| **People** | CIO, COO, CTO, cloud director, cross-functional leaders | Culture evolution; transformational leadership; **cloud fluency**; **workforce transformation**; change acceleration; organization design; organizational alignment |
| **Governance** | Chief transformation officer, CIO, CTO, CFO, CDO, CRO | Program and project mgmt; benefits mgmt; **risk mgmt**; **cloud financial management**; application portfolio mgmt; data governance; data curation |
| **Platform** | CTO, technology leaders, architects, engineers | Platform and data architecture; platform and data engineering; provisioning and orchestration; modern app development; **CI/CD** |
| **Security** | CISO, CCO, internal audit leaders, security architects and engineers | Security governance and assurance; IAM; threat detection; vulnerability mgmt; infrastructure and data protection; application security; incident response |
| **Operations** | Infrastructure and operations leaders, SREs, IT service managers | Observability; event mgmt (AIOps); incident and problem mgmt; change and release mgmt; performance and capacity mgmt; configuration and **patch** mgmt; availability and continuity; application mgmt |

Business, People, Governance = business capabilities. Platform, Security, Operations = technical capabilities.

**Business outcomes (exam guide):** reduced business risk; improved ESG performance; increased revenue; increased operational efficiency.

**Transformation domains:** Technology, Process, Organization, Product.

**Transformation phases:** **Envision** (show how cloud accelerates outcomes) → **Align** (find capability gaps across the six perspectives) → **Launch** (pilots in production) → **Scale** (expand to full scale, sustain benefits).

## If the question says X, answer Y

- "Recover automatically from failure", "multi-AZ", "test recovery" → **Reliability**
- "Choose the right instance type for speed", "serverless", "lower latency globally" → **Performance efficiency**
- "Turn off idle resources", "pay only for what you use", "attribute costs" → **Cost optimization**
- "Reduce energy or carbon footprint", "maximize utilization" for the environment → **Sustainability**
- "Operations as code", "small reversible changes", "learn from operational failures" → **Operational excellence**
- "Least privilege", "traceability", "encrypt in transit and at rest" → **Security**
- "Review my workload against best practices" → **AWS Well-Architected Tool**
- "Train staff, build cloud skills, manage organizational change" → **CAF People**
- "Manage cloud spend, risk, benefits, program management" → **CAF Governance**
- "Business strategy, product, innovation, data monetization" → **CAF Business**
- "Architecture, CI/CD, provisioning, modern app development" → **CAF Platform**
- "Monitoring, patching, incident management, SRE" → **CAF Operations**
- "Identity, threat detection, data protection, CISO" → **CAF Security**
- "Run pilots in production" → **Launch** phase; "identify capability gaps" → **Align** phase

Notes: [[1.2 Design Principles - Well-Architected Framework]] · [[1.3 Migration Strategies and AWS CAF]] · Cards: [[Flashcards - Domain 1]]
