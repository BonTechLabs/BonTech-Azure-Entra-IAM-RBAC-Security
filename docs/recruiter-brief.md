# Cloud Identity Security Case Study — Recruiter Brief

## The challenge

A fictional consulting company needs consistent identity administration across IT, Security, HR, Finance and Engineering. Giving a Security IAM analyst an overly broad User Administrator role increases the risk of unnecessary directory modification.

## My approach

**1. Organize identity.** Provisioned fictional employee identities and five assigned-membership security groups, then inspected Security department membership.

**2. Reduce privilege.** Replaced User Administrator with the narrower built-in Directory Readers role for a read-only analyst.

**3. Test the real outcome.** Used the analyst's separate browser session to confirm that user information remained visible but Edit properties and Reset password controls were unavailable.

**4. Exercise offboarding.** Disabled a dedicated test identity and revoked sign-in sessions through the admin portal.

**5. Check independent evidence.** Examined audit logs for account disablement and refresh-token validity updates.

**6. Assess authentication exposure.** Reviewed registered Microsoft Authenticator and Windows Hello passkey methods and a user-evaluated methods policy with FIDO2 enabled and SMS disabled.

## Evidence-backed impact

| Security capability | Evidence-backed achievement |
|---|---|
| Least privilege | Removed broad User Administrator assignment; Directory Readers verified |
| Restricted access | Two modification-oriented actions unavailable in test session |
| Departmental organization | Five security groups; four direct members shown in Security group |
| Employee offboarding | Test account showed Disabled; session revocation succeeded |
| Auditability | User-management and session-related audit events inspected |
| Authentication posture | FIDO2 and Authenticator options reviewed for one identity |

**No invented metrics:** This lab did not measure percentage risk reduction, production incident reductions, automated scan volumes, or organization-wide MFA enforcement.

## What I would improve next

Validate all effective app/resource entitlements, enforce phishing-resistant MFA using appropriate licensing and policy, assign group owners and run access reviews, test blocked post-disable sign-in and active app-session behavior, define audit retention, and automate repeatable checks.

## Interview discussion prompts

- Why did Directory Readers fit the analyst's job better than User Administrator?
- Why is a screenshot of role assignment insufficient evidence of least privilege?
- What is the difference between disabling an account and revoking sessions?
- Why does FIDO2 resist credential phishing better than SMS codes?
- Why must group membership be distinguished from permissions on an application or Azure resource?

[Read the full implementation](implementation.md) · [Inspect test results](../tests/validation-matrix.md) · [See evidence register](../evidence/README.md) · [See architecture](../diagrams/architecture.md)

*All work was performed in a fictional educational lab; no employer production environment is claimed.*
