---
tags:
  - clf-c02
  - services
  - services/end-user-computing
category: "End-User Computing"
status: not-started
---
# Services: End-User Computing

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

Exam guide 3.8 asks you to identify "the services that can present the output of virtual machines (VMs) on end-user machines". The objective is covered in [[3.8 Other In-Scope Service Categories]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#Amazon AppStream 2.0]] | Streams individual desktop applications to a browser | "Stream an application", "access one app from any device", "no full desktop" |
| [[#Amazon WorkSpaces]] | Persistent virtual desktops (DaaS) in the cloud | "Virtual desktop", "VDI", "remote employees need a full Windows/Linux desktop" |
| [[#Amazon WorkSpaces Web]] | Secure browser access to internal sites and SaaS | "Secure browser", "internal websites", "SaaS apps", "no data on the device" |

> [!tip] Desktop, app, or browser?
> Whole desktop: **WorkSpaces**. One application: **AppStream 2.0**. Only websites and web/SaaS apps: **WorkSpaces Web**. In all three, data stays in AWS rather than on the user's device.

## Amazon AppStream 2.0

> [!summary] Application streaming service that provides users with instant access to desktop applications from anywhere.

- **What it does:** Runs desktop applications on AWS and streams them to users, who access them through a web browser or client. Users get the application, not a whole desktop, and no application data is stored on their devices.
- **Choose it when:** Users need a specific desktop application (for example design or engineering software) on any device without installing it, or a SaaS vendor wants to deliver its desktop app through the browser.
- **Key facts:**
  - Streams ==applications==, not full persistent desktops.
  - Fully managed, scales automatically, pay-as-you-go.
  - Access through an HTML5 browser or the client app.
  - Data is not stored on the user's device.
- **Don't confuse with:** [[#Amazon WorkSpaces]] (full persistent desktop per user) and [[#Amazon WorkSpaces Web]] (browser access to websites only).
- **Docs:** [What is Amazon WorkSpaces Applications (formerly AppStream 2.0)?](https://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html)

Current status: AWS now calls this service Amazon WorkSpaces Applications; the AWS docs use that name on the AppStream 2.0 developer guide pages.

## Amazon WorkSpaces

> [!summary] Provision virtual, cloud-based desktops without the need to deploy hardware or install complex software.

- **What it does:** A desktop-as-a-service (DaaS) offering that gives each user a persistent virtual Windows or Linux desktop running in AWS. Users connect from laptops, tablets, thin clients, or browsers.
- **Choose it when:** A company needs virtual desktops (VDI) for remote or temporary workers, wants to avoid buying and managing desktop hardware, or wants data kept off endpoint devices.
- **Key facts:**
  - ==Full virtual desktop== per user, Windows or Linux.
  - Billed monthly or hourly per WorkSpace.
  - Integrates with Microsoft Active Directory through AWS Directory Service.
  - Replaces on-premises VDI hardware with a managed service.
- **Don't confuse with:** [[#Amazon AppStream 2.0]] (one application streamed, not a desktop) and [[Services - Compute#Amazon EC2|Amazon EC2]] (servers you manage, not managed desktops).
- **Docs:** [What is Amazon WorkSpaces?](https://docs.aws.amazon.com/workspaces/latest/adminguide/amazon-workspaces.html)

## Amazon WorkSpaces Web

> [!summary] Facilitates secure browser access to internal websites and SaaS applications.

- **What it does:** Gives employees a secure, managed web browser running in AWS that streams to their local browser. They can reach internal websites and SaaS applications, and no web content or data is stored on the local device.
- **Choose it when:** Workers only need web-based tools (intranet sites, SaaS apps), and the company wants to reduce data-leak risk without managing full virtual desktops or VPN client software.
- **Key facts:**
  - ==Browser-only== access; no full desktop.
  - No data stored on the end-user device.
  - Admins control policies such as clipboard, printing, and download restrictions.
  - Integrates with SAML 2.0 identity providers.
- **Don't confuse with:** [[#Amazon WorkSpaces]] (full desktop) and [[#Amazon AppStream 2.0]] (desktop applications, not websites).
- **Docs:** [What is Amazon WorkSpaces Secure Browser?](https://docs.aws.amazon.com/workspaces-web/latest/adminguide/what-is-workspaces-web.html)

Current status: Renamed Amazon WorkSpaces Secure Browser on May 20, 2024. AWS has since placed WorkSpaces Secure Browser in maintenance (no new customers; AWS General Reference lifecycle page).

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
