# BonTech Consulting | Microsoft Entra ID IAM, RBAC & Identity Security

> **Hands-on cloud identity security lab** | Microsoft Entra ID · Role-Based Access Control · Least Privilege · FIDO2 · Audit Logs · Account Lifecycle

**Project type:** Guided, simulated-enterprise security implementation  
**Environment:** Fictional BonTech Consulting directory; not a production deployment  
**Status:** Technical walkthrough and selected security tests completed; publication of redacted screenshot evidence in progress.

## Executive summary

Designed and validated identity and access management controls in a Microsoft Entra ID lab modeling a multi-department organization. The exercise demonstrates the transition from an overly permissive administrative role to **Directory Readers**, confirms restricted effective access in a separate sign-in session, tests employee offboarding controls, and inspects directory audit events and evaluated authentication methods.

This repository emphasizes **what was built, how it was tested, what the evidence supports, and what remains unverified**. It does not represent an enterprise-wide security certification or production implementation.

## Demonstrated outcomes

| Area | Hands-on result | Evidence status |
|---|---|---|
| Identity provisioning | Fictional departmental user accounts and dedicated nonprivileged test identity; 22 users reported during project | Project record; screenshot evidence to be sanitized |
| Security groups | Five cloud-managed, assigned-membership departmental security groups | Group listing inspected |
| Membership validation | `BT-Security-Users` displayed four direct user members | Members view inspected |
| Privilege reduction | David Collins changed from **User Administrator** to **Directory Readers** | Role assignment verified |
| Effective access | David's separate session could view a test identity but **Edit properties** and **Reset password** were unavailable | UI test verified for these operations |
| Leaver controls | Dedicated RBAC test user disabled | Disabled status verified |
| Session revocation | Entra portal confirmed successful action | Success notification verified |
| Audit trail | Successful user-management and `Update StsRefreshTokenValidFrom` events reviewed | Audit log observed |
| Authentication review | Microsoft Authenticator + Windows Hello passkey registered for David; evaluated FIDO2 enabled and SMS disabled | **Individual user evaluation**, not proof of tenant-wide enforcement |

## Architecture

[View the logical architecture](diagrams/architecture.md)

```text
                         Microsoft Entra ID tenant
                          (BonTech Consulting lab)
                                     |
               +---------------------+--------------------+
               |                     |                    |
       Fictional users        Security groups      Directory admin roles
       + test identity        IT / Security /      Global Admin (lab)
                              HR / Finance /       Directory Readers (David)
                              Engineering                   |
               |                     |                    |
          Authentication       Departmental          Effective permission
          methods review       membership             validation
               |                     |                    |
       Authenticator/FIDO2     4 Security users       Edit/reset unavailable
               +---------------------+--------------------+
                                     |
                           Identity security operations
                       Disable user · Revoke sessions
                                     |
                                Audit logs
```

> **Boundary note:** Group membership does not automatically confer Azure resource privileges or application entitlements. Separate resource/application assignments would be required.

## Security validation

See [Validation matrix](tests/validation-matrix.md) for test objectives, observed behavior, and limits of each result.

**Representative security scenario:** An IAM analyst only needs to inspect user records. Granting User Administrator would permit unnecessary user-management operations. The role was removed, Directory Readers was assigned, and testing in the analyst's own browser session confirmed read availability while user-edit and password-reset actions were disabled.

**Offboarding scenario:** A dedicated test account was disabled and sessions revoked. The audit log recorded the administrative operation. Revocation of refresh tokens does **not** guarantee immediate invalidation of every already-issued access token or application-specific session.

## Documentation index

| Resource | Purpose |
|---|---|
| [Architecture](diagrams/architecture.md) | Logical boundaries, control flows and trust assumptions |
| [Implementation record](docs/implementation.md) | Scope, environment and configurations actually examined |
| [Validation matrix](tests/validation-matrix.md) | Positive/negative tests and evidence limitations |
| [Evidence register](evidence/README.md) | Screenshot inventory and public-sharing redaction checklist |
| [Security review](security/security-review.md) | Risks, licensing constraints and prioritized next steps |
| [Engineering decisions](docs/engineering-decisions.md) | Least-privilege and authentication design rationale |

## Key engineering lessons

- **Verify effective access** with the affected account, not only the administrator's role assignment page.
- **Limit blast radius** by using read-only directory roles for inspection-only responsibilities.
- **Handle movers and leavers** by reviewing accumulated group and role access, disabling departed identities, and revoking sessions.
- **Prefer phishing-resistant authentication** such as FIDO2 passkeys for high-risk identities.
- **Audit evidence is action evidence**, not blanket proof that all sessions, permissions, or enterprise controls are secure.

## Explicit limitations

- This is a fictional training tenant, not a production customer deployment.
- The authentication-methods screenshot represents an **evaluated policy for one user**; tenant-wide MFA enforcement was **not** established.
- Conditional Access, Privileged Identity Management, full identity governance, automated policy deployment, and automated incident remediation were **not** demonstrated.
- A full audit of all Azure resource assignments and application entitlements was **not** performed.
- Screenshot evidence will be added only after privacy/security review; no raw session imagery or account details are published here.

## Portfolio presentation

**Role exercised:** Cloud Identity & Access Security Engineer (hands-on lab)  
**Tools:** Microsoft Entra ID, Azure portal, Microsoft Authenticator, Windows Hello, Microsoft Entra audit logs  
**Skills:** IAM, RBAC, least privilege, group governance, phishing-resistant authentication concepts, offboarding, test design, audit analysis, evidence-based reporting

**Repository maintained by:** [TAMUYEH1993](https://github.com/TAMUYEH1993)

---
*This repository documents a guided educational lab. Security screenshots must be redacted before public upload. No real employer or production system is represented.*
