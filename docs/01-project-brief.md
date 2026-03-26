# Project Brief – Cloud-Native IAM Lab

## Objective

Design and implement a **cloud-native Identity and Access Management (IAM) environment** for a healthcare organization using modern security and Zero Trust principles.

The environment must be:

* secure
* scalable
* cost-efficient
* aligned with real-world IAM practices

---

## Company Overview

**Company Name:** Northstar Health
**Industry:** Healthcare Technology
**Headquarters:** London, United Kingdom
**Other Locations:** Manchester and Remote Workforce
**Total Employees (Simulated):** ~300

Northstar Health develops digital healthcare platforms used by clinics and hospitals. The company handles sensitive data, requiring strong identity and access controls.

---

## Business Structure

### Departments

* HR
* Finance
* IT
* Security
* Sales
* Customer Support
* Operations

Each department has different access requirements and risk levels.

---

## Identity Types

### Workforce Identities

Standard employee accounts assigned based on department.

### Privileged Identities

Separate administrative accounts used only for elevated tasks.

### Contractors

Temporary identities with limited and time-bound access.

### Guest Users (B2B)

External partner users with restricted collaboration access.

### Application Identities

Service principals and managed identities used for automation and application access.

---

## Admin Model

Administrative access is separated from standard user accounts.

### Admin Roles

* IAM Admin (user and group management)
* Security Admin (Conditional Access and monitoring)
* Intune Admin (device compliance and management)
* Global Reader (audit and visibility)

### Design Principles

* No shared admin accounts
* No permanent high privilege where avoidable
* Admin roles separated from daily-use accounts
* Privileged access to be time-bound (implemented later with PIM)

---

## Emergency Access (Break-Glass)

Two emergency accounts are created:

* emergency1@
* emergency2@

### Design Approach

* Used only for emergency recovery
* Excluded from Conditional Access policies
* Not used for daily administration
* Monitored through logs and alerts
* Designed to avoid tenant lockout
* Designed to avoid single points of failure

This reflects modern IAM thinking where security must be balanced with recoverability.

---

## Application Landscape

### Core Platforms

* Microsoft 365
* Azure Portal
* Intune Admin Center

### Business Applications

* HR system
* Finance system
* CRM platform
* Ticketing system

### Identity-Integrated Applications

* One SaaS application using SAML
* One internal application using OpenID Connect

---

## Device Strategy

### Device Types

* Corporate Windows laptops
* Mobile devices (iOS and Android)
* Contractor unmanaged devices
* Secure admin workstations

### Access Principles

* Sensitive access requires compliant devices
* Admin actions require trusted devices
* Mobile access is restricted or controlled
* Contractors have limited access paths

---

## Security Requirements

### Authentication

* MFA required for all users
* Stronger authentication for admins
* Legacy authentication blocked
* Passwordless supported where possible

### Authorization

* Group-based access model
* Least privilege enforced
* No direct user-to-app assignments
* Admin access separated and controlled

### Device-Based Access

* Compliance required for sensitive resources
* Admin access restricted to trusted devices

### Governance

* Contractor access expires automatically
* Guest access reviewed regularly
* Privileged roles reviewed regularly

### Monitoring

* Sign-in activity monitored
* Administrative actions audited
* Access patterns reviewed

---

## Risk Scenarios

The IAM system must mitigate:

* Phishing leading to account compromise
* Over-privileged administrative access
* Users retaining access after role changes
* Delayed or incomplete offboarding
* Access from unmanaged or insecure devices
* Excessive access for guest users
* Long-lived contractor access

---

## IAM Objectives

* Implement a cloud-only identity architecture
* Enforce Zero Trust access principles
* Apply least privilege across all access
* Secure privileged access
* Enable secure external collaboration
* Automate identity lifecycle processes
* Provide full auditability and monitoring

---

## Success Criteria

The project is successful when:

* All users are protected by strong authentication
* No permanent privileged access exists
* Access is group-based and structured
* Sensitive access requires compliant devices
* External and contractor access is governed
* Identity lifecycle processes are controlled
* Logs provide clear visibility into access and activity

---

## Scope Notes

This environment is designed to simulate a **300-user enterprise**, but is implemented using a **small representative identity set** to validate IAM controls in a cost-efficient manner.

