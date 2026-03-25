# Project Brief – Cloud-Native IAM Lab

## Project Name

Cloud-Native Enterprise IAM Lab

---

## Company Overview

**Company Name:** Northstar Health
**Industry:** Healthcare Technology
**Headquarters:** London, United Kingdom
**Other Locations:** Manchester and Remote Workforce
**Total Employees:** ~300

Northstar Health develops digital healthcare platforms used by clinics and hospitals across the UK. The company handles sensitive patient-adjacent data, requiring strong identity and access controls.

---

## Business Structure

### Departments

* HR (15 users)
* Finance (20 users)
* IT (10 users)
* Security (5 users)
* Sales (80 users)
* Customer Support (70 users)
* Operations (100 users)

---

## Identity Types

### Workforce Identities

Standard employee accounts assigned by department.

### Privileged Identities

Separate admin accounts used only for administrative tasks.

### Contractors

Temporary identities with restricted and time-bound access.

### Guest Users (B2B)

External partner users with limited collaboration access.

### Application Identities

Service principals and managed identities for automation.

---

## Admin Role Model

| Role           | Purpose                            |
| -------------- | ---------------------------------- |
| IAM Admin      | User, group, lifecycle, governance |
| Security Admin | Conditional Access, monitoring     |
| Intune Admin   | Device compliance and policies     |
| Global Reader  | Audit and visibility only          |

### Admin Rules

* No standing Global Admin usage
* Admin accounts separate from user accounts
* Privileged access must be just-in-time (PIM)

### Emergency Access

* Two break-glass accounts
* Excluded from Conditional Access
* Strong password and monitored usage

---

## Application Landscape

### Core Platforms

* Microsoft 365
* Azure Portal
* Intune Admin Center

### Business Applications

* HR Management System
* Finance Approval System
* CRM Platform
* Ticketing System

### Identity-Integrated Apps

* One SaaS app using SAML
* One internal web app using OpenID Connect

---

## Device Strategy

### Device Types

* Corporate Windows laptops
* Mobile devices (iOS and Android)
* Contractor unmanaged devices
* Admin secure workstations

### Trust Requirements

* Admin access requires compliant device
* Finance access requires compliant device
* Mobile access allowed with restrictions
* Contractors limited access

---

## Security Requirements

### Authentication

* MFA required for all users
* Stronger authentication for admins
* Legacy authentication blocked
* Passwordless encouraged

### Authorization

* Access assigned via groups only
* Least privilege enforced
* Admin roles separated from user roles
* Privileged access time-bound

### Device-Based Access

* Sensitive apps require compliant devices
* Admin actions blocked from unmanaged devices

### Governance

* Contractor access expires automatically
* Guest access reviewed regularly
* Privileged roles reviewed regularly

### Monitoring

* Sign-in logs monitored
* Admin activity audited
* Conditional Access validated

---

## Risk Scenarios

* Phishing leading to account compromise
* Over-privileged admin accounts
* Users retaining access after role change
* Leavers not deprovisioned quickly
* Unmanaged device access
* Guest overexposure
* Contractor access not removed

---

## IAM Objectives

* Cloud-only identity architecture
* Centralized identity via Microsoft Entra ID
* Strong authentication and Zero Trust
* Device-aware access using Intune
* Privileged access control using PIM
* Controlled external collaboration
* Lifecycle automation
* Full auditability

---

## Success Criteria

* MFA enforced for all users
* No permanent privileged access
* Group-based access model
* Device compliance enforced
* Guest and contractor governance in place
* Identity lifecycle automated
* Logs provide full visibility

