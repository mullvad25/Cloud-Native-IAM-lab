# Cloud-Native IAM Lab

## Overview

This project simulates a **cloud-native Identity and Access Management (IAM) environment** for a healthcare technology company, **Northstar Health**.

The goal is to design, implement, and secure an enterprise IAM system using **modern, cloud-first and Zero Trust principles**, while keeping the environment **cost-efficient and scalable**.

This lab is designed to simulate a **300-user organization**, implemented using a **small representative identity set** to validate IAM controls.

---

## Objectives

* Design a cloud-only IAM architecture using Microsoft Entra ID
* Implement strong authentication (MFA and modern methods)
* Enforce Conditional Access using Zero Trust principles
* Manage device-based access using Intune
* Control privileged access using Just-In-Time (PIM)
* Integrate applications using SAML and OpenID Connect
* Implement identity lifecycle (joiner, mover, leaver)
* Apply governance (access packages and access reviews)
* Monitor and respond to identity-based threats
* Automate IAM using scripting and Infrastructure as Code (Terraform)

---

## Key Design Principles

* Cloud-first identity (no on-prem dependency)
* Least privilege access model
* Group-based access control (no direct assignments)
* Separation of user and admin identities
* Just-in-time privileged access
* Device-aware access control
* Continuous monitoring and auditability

---

## Architecture

(To be added in /diagrams/architecture.png)

---

## Technologies Used

* Microsoft Entra ID
* Conditional Access
* Microsoft Intune
* Privileged Identity Management (PIM)
* Azure RBAC
* PowerShell and Microsoft Graph
* Terraform (introduced in later phase)

---

## Project Structure

```text
docs/        → IAM design and implementation by phase  
scripts/     → automation scripts  
diagrams/    → architecture and flow diagrams  
screenshots/ → evidence of configurations  
notes/       → learning, troubleshooting, and progress tracking  
```

---

## Learning Approach

This project is built in **learning mode**, meaning each phase includes:

* Concept: why the control exists
* Implementation: how it is configured
* Validation: how it is tested
* Failure Scenario: what happens if misconfigured
* Lessons Learned: key takeaways

This ensures deep understanding of IAM, not just configuration.

---

## Simulated Environment

**Company:** Northstar Health
**Industry:** Healthcare Technology
**Locations:** London, Manchester, Remote UK Workforce
**Scale (Simulated):** ~300 users
**Actual Lab Size:** ~10–15 identities

---

## IAM Capabilities Covered

* Identity architecture and design
* Authentication and MFA strategy
* Conditional Access policy design
* Device compliance and access control
* Privileged access management
* Application integration (SSO)
* Identity lifecycle management
* External identity (B2B)
* Governance and access reviews
* Monitoring and incident response
* IAM automation and Infrastructure as Code

---

## Outcome

This project demonstrates the ability to:

* Design secure IAM architectures
* Implement Zero Trust access controls
* Apply least privilege principles
* Identify and mitigate identity risks
* Understand IAM failure scenarios
* Translate IAM design into automation

---

## Notes

This environment is intentionally built using a **minimal identity set** to reduce cost while preserving **enterprise-level design and security principles**.

