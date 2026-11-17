---
tags:
  - clf-c02
  - cheat-sheet
---
# IAM Essentials

IAM is **global** and **free**. Default = deny. Explicit allow grants. **Explicit deny always wins.**

## Identities

| Identity | Credentials | Use for |
| --- | --- | --- |
| Root user | Email + password | Only root-only tasks; lock away with MFA |
| IAM user | Long-term password and/or access keys | One person or app (prefer Identity Center for people) |
| IAM group | None; cannot sign in; no nesting | Attach policies by job function |
| IAM role | **Temporary** (STS); assumed | EC2/Lambda access to AWS, cross-account, federation |

## Policies

| Type | Reusable | Who writes |
| --- | --- | --- |
| AWS managed | Yes | AWS |
| Customer managed | Yes | You (best for least privilege) |
| Inline | No, one identity | You |

Also: resource-based (S3 bucket policy), SCPs (Organizations, max permissions, grant nothing), permissions boundaries.

## Root user

**Protect:** MFA, no access keys, strong password, admin identity for daily work, monitor root sign-ins.

**Root-only tasks:** change root email, root password, or root access keys · close (or reopen) the account · restore permissions for a locked-out sole admin · activate IAM access to Billing · view certain tax invoices · sign up for GovCloud · register as RI Marketplace seller · enable S3 MFA Delete · fix an S3 bucket policy or SQS queue policy that denies all principals.

## Credentials

- **Password policy:** length, complexity, expiration, reuse; IAM users only.
- **Access keys:** CLI/SDK/API; never embed in code; rotate; prefer roles.
- **MFA:** authenticator app, passkey or FIDO2 security key, hardware token.
- **Secrets Manager:** secrets with **automatic rotation**; per-secret cost.
- **Parameter Store (Systems Manager):** config and SecureString; free standard tier; no built-in rotation.

## Identity options

| Need | Service |
| --- | --- |
| Employees, single sign-on to many accounts and apps | IAM Identity Center (AWS SSO) |
| App end users, social login, sign-up | Amazon Cognito |
| Microsoft Active Directory | AWS Directory Service |
| Use corporate IdP without IAM users | Federation (SAML 2.0 / OIDC) |
| Users in account A work in account B | Cross-account IAM role |
| Share resources across accounts | AWS RAM |

## Access reports

| Tool | Shows |
| --- | --- |
| Credential report | Every user's password, access key, MFA status |
| Access advisor / last accessed | Services used and when; trim unused permissions |
| Access Analyzer | Resources shared outside your account or org; unused access; policy generation |

## If the question says X, answer Y

- "App on EC2 needs S3 access" → IAM role
- "Reusable least-privilege custom permissions" → customer managed policy
- "Grant same permissions to 20 developers" → IAM group
- "First step after creating an account" → MFA on root, create admin identity
- "Single sign-on for workforce" → IAM Identity Center
- "Mobile app login with Google" → Cognito
- "Rotate DB credentials" → Secrets Manager
- "Restrict what a member account can do" → SCP in AWS Organizations
- "Which users have no MFA" → credential report
- "S3 bucket shared publicly or with another account" → IAM Access Analyzer

Details: [[2.3 Access Management and IAM]] · Cards: [[Flashcards - Domain 2]]
