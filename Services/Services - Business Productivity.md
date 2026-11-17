---
tags:
  - clf-c02
  - services
  - services/business-productivity
category: "Business Productivity"
status: not-started
---
# Services: Business Productivity

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

The exam guide calls this category "Business Productivity" in its appendix and "business application services" in task statement 3.8; the reference guide calls it **Business Applications**. Same two services either way. Concepts are in [[3.8 Other In-Scope Service Categories]].

| Service | What it is (under ten words) | Cue in a question |
|---|---|---|
| [[#Amazon Connect\|Amazon Connect]] | Omnichannel cloud contact center | "call center", "contact center", "customer service agents", "IVR" |
| [[#Amazon Simple Email Service (Amazon SES)\|Amazon SES]] | Send and receive email at scale | "marketing email", "transactional email", "bulk email", "send from our domain" |

## Amazon Connect

> [!summary] Omnichannel cloud contact center.

- **What it does:** Amazon Connect lets a business set up a cloud-based customer contact center in minutes, with no phone hardware or telephony infrastructure to buy. Agents handle voice calls, chat, and tasks from a web browser, and the business designs call flows (who hears what menu, which queue a caller goes to) with a drag-and-drop editor.
- **Choose it when:** the question mentions a "call center", "contact center", "customer support agents taking calls", "interactive voice response (IVR)", or "omnichannel customer service".
- **Key facts:**
  - "Omnichannel" means voice, chat, and other channels in one service with one agent interface.
  - Pay-as-you-go based on usage (for example per minute of calls), with no long-term commitment or upfront licence.
  - Integrates with Amazon Lex for conversational chatbots and voice bots in call flows, and with Contact Lens for call analytics such as sentiment and transcription.
  - Same technology Amazon uses for its own customer service.
- **Don't confuse with:** **Amazon Lex** (builds the chatbot or voice bot; Connect is the whole contact center that can use Lex). **Amazon SNS** (sends automated notifications; no human agents). **AWS Support** (AWS's own help for AWS customers, not a contact center you run).
- **Docs:** [What is Amazon Connect?](https://docs.aws.amazon.com/connect/latest/adminguide/what-is-amazon-connect.html)

## Amazon Simple Email Service (Amazon SES)

> [!summary] Send and receive emails through existing email addresses and domains.

- **What it does:** SES is a cloud email service for sending email from your applications using your own domain and addresses. It handles bulk marketing campaigns, transactional messages (order confirmations, password resets), and can also receive incoming email and pass it to S3, Lambda, or SNS.
- **Choose it when:** the question says "send marketing emails", "send transactional emails such as order confirmations", "bulk email", "email from our own domain", or "HTML-formatted email to customers".
- **Key facts:**
  - Sends via SMTP interface or the SES API; pay for what you send, no minimum commitment.
  - Supports email authentication (SPF, DKIM, DMARC) and reputation and deliverability tools, including dedicated IP addresses.
  - Can receive email and trigger actions (store in S3, invoke Lambda, notify SNS).
  - Recipients do not need to subscribe to anything; you send to any address (unlike SNS email).
- **Don't confuse with:** **Amazon SNS** (pub/sub notifications; the email protocol sends plain notification text only to confirmed topic subscribers, not branded campaigns). **Amazon Pinpoint** (multichannel marketing engagement; not on the in-scope list). **Amazon WorkMail** (business mailbox and calendar for employees; not in scope).
- **Docs:** [What is Amazon SES?](https://docs.aws.amazon.com/ses/latest/dg/Welcome.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
