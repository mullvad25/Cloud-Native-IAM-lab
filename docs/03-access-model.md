# Phase 3 – Access Model

## Objective

Design a scalable and auditable access model for the Northstar Health IAM lab using Microsoft Entra ID group-based access control principles.

This phase focuses on separating identity from access so that permissions are not assigned directly to users. Instead, access is structured through layered security groups that support cleaner administration, easier lifecycle management, and reduced privilege sprawl.

---

## Environment Context

* Organization: Northstar Health
* Industry: Healthcare Technology
* Locations: London (HQ), Manchester, Remote UK workforce
* IAM Platform: Microsoft Entra ID
* Architecture: Cloud-native only
* Security Model: Zero Trust aligned
* Access Model Goal: Group-based, scalable, least-privilege oriented

---

## Problem Statement

If access is assigned directly to users, the environment becomes difficult to manage and audit. Over time this leads to:

* inconsistent permissions
* manual access changes
* privilege creep
* weak joiner, mover, leaver processes
* poor scalability

To avoid this, access must be abstracted away from individual accounts and assigned through structured groups.

---

## Design Principles

The Phase 2 access model was built using the following principles:

* Access should be assigned to groups, not directly to users
* Identity and access should be separated
* Group naming should reflect function clearly
* Group nesting should support future lifecycle automation
* Access design should remain simple enough to audit
* Privileged access should remain distinct from standard business access

---

## Access Model Overview

The access model uses a layered design:

```text
User → SG-* → AG-* → Resource
```

### Model Meaning

* **User** = individual identity
* **SG** = Security Group representing who the user is
* **AG** = Access Group representing what the user can access
* **Resource** = application, system, or service

This model ensures that users inherit access through group membership instead of direct assignment.

---

## Group Types

### 1. Organizational Groups

These groups were created in Phase 1 and represent department or workforce identity.

Examples:

* SG-HR
* SG-Finance
* SG-IT
* SG-Sales
* SG-Support
* SG-Operations
* SG-All-Employees

These answer the question:

**Who is the user?**

---

### 2. Access Groups

These groups were created in Phase 2 and represent access intent.

Examples:

* AG-HR-Apps
* AG-Finance-Apps
* AG-IT-AdminTools
* AG-Sales-CRM
* AG-Support-Tickets
* AG-Operations-Core

These answer the question:

**What should the user be able to access?**

---

## Naming Convention

### Organizational Groups

Format:

`SG-<Department>`

Examples:

* SG-HR
* SG-Finance
* SG-IT

---

### Access Groups

Format:

`AG-<Department>-<AccessPurpose>`

Examples:

* AG-HR-Apps
* AG-Finance-Apps
* AG-IT-AdminTools
* AG-Sales-CRM

This naming model makes group purpose immediately visible and supports future governance and automation.

---

## Access Group Inventory

The following access groups were created:

* AG-HR-Apps
* AG-Finance-Apps
* AG-IT-AdminTools
* AG-Sales-CRM
* AG-Support-Tickets
* AG-Operations-Core

All groups were created as:

* Security groups
* Assigned membership
* Not role-assignable
* Owned by `iam-admin@`

---

## Group Ownership

All AG-* groups are owned by:

* iam-admin@

### Design Decision

Ownership was centralized under the IAM administration account rather than department users.

This was done because:

* governance processes are not yet implemented
* access reviews are not yet in place
* centralized ownership reduces unmanaged changes
* the lab is still in an early controlled state

This reflects a deliberate design choice to prioritize clarity and control before decentralizing ownership in later governance phases.

---

## Group Nesting Design

Organizational groups were nested into access groups as follows:

| Organizational Group | Access Group       |
| -------------------- | ------------------ |
| SG-HR                | AG-HR-Apps         |
| SG-Finance           | AG-Finance-Apps    |
| SG-IT                | AG-IT-AdminTools   |
| SG-Sales             | AG-Sales-CRM       |
| SG-Support           | AG-Support-Tickets |
| SG-Operations        | AG-Operations-Core |

### Example Access Path

An HR user follows this path:

```text
alice.hr@ → SG-HR → AG-HR-Apps → Resource
```

This means access can later be granted to the AG-HR-Apps group without assigning anything directly to Alice.

---

## Design Decision: No Direct User Membership in Access Groups

Users were not added directly to AG-* groups.

Instead, only SG-* groups were nested inside AG-* groups.

### Reasoning

This preserves a clean separation between:

* identity grouping
* access grouping

It also improves:

* consistency
* lifecycle handling
* auditability
* future automation readiness

---

## Design Decision: No App Assignment Yet

Applications and enterprise app assignments were intentionally deferred.

Phase 2 focuses only on access structure, not application onboarding.

This keeps the design clean and ensures that access logic is understood before technical integrations are introduced.

---

## Validation Performed

The following checks were completed:

* all required AG-* groups were created
* each AG-* group has `iam-admin@` as owner
* each SG-* group was nested into the correct AG-* group
* AG-* groups do not contain direct user members
* organizational groups remain separate from access groups
* access path design is ready for future application assignment

---

## Failure Scenarios Considered

### Direct User-to-Access Assignment

If access is assigned directly to users:

* permissions become inconsistent
* onboarding and offboarding become manual
* auditing becomes difficult
* lifecycle controls weaken

---

### Mixing Identity Groups and Access Groups

If SG-* groups are used directly for app assignments without an access abstraction layer:

* access design becomes rigid
* future changes become harder
* governance loses clarity

---

### Direct Membership in AG-* Groups

If users are added directly to AG-* groups:

* the access model becomes inconsistent
* hidden privilege paths emerge
* lifecycle management becomes error-prone

---

### Weak Naming Standards

If naming is inconsistent:

* group purpose becomes unclear
* audit work becomes harder
* automation becomes more difficult later

---

## Key Lessons Learned

* identity and access are not the same thing
* access should be abstracted away from users
* group nesting improves scalability
* layered group design supports cleaner IAM operations
* structured naming is part of security design, not just administration
* a strong access model makes future lifecycle and governance work much easier

---

## Phase Outcome

At the end of this phase, the lab now has a structured group-based access model that separates:

* who a user is
* what a user can access

The resulting model is:

```text
User → SG-* → AG-* → Resource
```

This provides a scalable foundation for future phases including:

* lifecycle management
* authentication policy targeting
* application access assignment
* governance and access reviews
* eventual automation

---

## Screenshot Suggestions

Recommended screenshots for this phase:

1. Access groups overview
2. Example AG-* group showing owner
3. Example AG-* group membership showing nested SG-* group
4. Multiple AG-* groups visible in group list
5. Example access path explanation in documentation or diagram

---

## Summary

Phase 2 established the logical access control structure for the tenant.

Instead of assigning access directly to users, the lab now uses a layered group-based model that improves auditability, maintainability, and security.

This phase lays the foundation for lifecycle controls in the next phase, where user changes will be managed through group membership rather than manual permission changes.

