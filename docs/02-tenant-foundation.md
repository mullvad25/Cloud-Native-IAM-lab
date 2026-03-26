# Tenant Foundation (Phase 1)

## Objective

Establish a clean, scalable, and secure cloud-only identity foundation using Microsoft Entra ID.

This phase focuses on:

* Structuring identities correctly
* Separating administrative access
* Implementing a group-based model
* Preparing the environment for secure access control

---

## Concept

The tenant foundation defines how identities are structured and managed.

Key IAM principles applied in this phase:

* Separation of duties (admin vs user accounts)
* Least privilege access
* Group-based access control
* Identity standardization through naming conventions

A strong foundation ensures that all future IAM controls (Conditional Access, PIM, governance) can be implemented consistently and securely.

---

## Design

### Naming Conventions

#### Users

Format:
firstname.department@

Examples:

* alice.hr@
* bob.finance@
* charlie.it@

---

#### Admin Accounts

Format:
role-admin@

Examples:

* iam-admin@
* sec-admin@
* intune-admin@
* reader-admin@

---

#### Groups

Format:
SG-[Department]

Examples:

* SG-HR
* SG-Finance
* SG-IT
* SG-Sales
* SG-Support
* SG-Operations
* SG-All-Employees

---

### Identity Structure

The environment uses a minimal identity set to simulate a larger enterprise.

#### Workforce Users

* alice.hr@
* bob.finance@
* charlie.it@
* diana.sales@
* emma.support@
* oliver.operations@

#### Admin Users (separate identities)

* iam-admin@
* sec-admin@
* intune-admin@
* reader-admin@

#### Emergency Accounts (Break-Glass)

* emergency1@
* emergency2@

#### Optional Test User

* test-risk@

---

### Group Model

#### Department Groups

* SG-HR
* SG-Finance
* SG-IT
* SG-Sales
* SG-Support
* SG-Operations

#### Global Group

* SG-All-Employees

#### Optional Admin Groups

* SG-Admins
* SG-Privileged-Eligible

---

### Role Assignments

| Account       | Role                   |
| ------------- | ---------------------- |
| iam-admin@    | User Administrator     |
| sec-admin@    | Security Administrator |
| intune-admin@ | Intune Administrator   |
| reader-admin@ | Global Reader          |

---

### Break-Glass Design

Emergency accounts are designed to:

* Provide access during lockout scenarios
* Be excluded from Conditional Access
* Avoid dependency on a single authentication method
* Be monitored for any usage

They are not used for daily administration.

---

## Implementation

### Step 1: Create Tenant

* Created a new Microsoft Entra tenant
* Region: United Kingdom

---

### Step 2: Create Users

* Created 6 workforce users
* Created 4 admin users
* Created 2 emergency accounts
* Created optional test account

---

### Step 3: Create Groups

* Created department-based security groups
* Created SG-All-Employees
* Assigned users to their respective groups
* Added all users to SG-All-Employees

---

### Step 4: Assign Roles

* Assigned least-privilege roles to admin accounts
* Avoided unnecessary Global Admin usage

---

### Step 5: Basic Hardening

* Reviewed default user permissions
* Reviewed external collaboration settings
* Ensured tenant is not over-permissive

---

## Validation

The following checks were performed:

* Users exist with correct naming convention
* Users are assigned to correct groups
* Admin roles are assigned to correct accounts
* No admin role is assigned to standard users
* Groups reflect department structure
* All users are included in SG-All-Employees

---

## Failure Scenario

### Scenario 1: No Group-Based Access

If access is assigned directly to users:

* Access becomes difficult to manage at scale
* Errors increase during role changes
* Inconsistent permissions across users

---

### Scenario 2: Admin Accounts Not Separated

If admins use normal user accounts:

* Increased risk of privilege misuse
* Higher impact if account is compromised
* No clear audit separation

---

### Scenario 3: Excessive Privileges

If too many Global Admins exist:

* Large blast radius if one account is compromised
* Difficult to track accountability

---

### Scenario 4: Poor Naming Conventions

If naming is inconsistent:

* Hard to manage identities
* Difficult to troubleshoot access issues
* Poor scalability

---

## Lessons Learned

* Group-based access is essential for scalability
* Admin accounts must always be separate from user accounts
* Least privilege reduces risk significantly
* Naming conventions are critical for long-term management
* A strong identity foundation simplifies all future IAM controls

---

## Screenshots

(Add the following screenshots)

* Users list
* Groups and memberships
* Role assignments
* Admin accounts

Path:
../screenshots/tenant-foundation/
