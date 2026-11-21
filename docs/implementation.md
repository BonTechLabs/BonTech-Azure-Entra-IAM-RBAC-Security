# Technical Implementation Record

## Environment

- **Business scenario:** BonTech Consulting (fictional organization)
- **Cloud identity platform:** Microsoft Entra ID, managed through Azure portal / Entra admin center.
- **Initial tenant domain:** omitted from public documentation to reduce account enumeration.
- **License in lab:** Microsoft Entra Free, as reported during the exercise.
- **Identity footprint:** 22 users reported; includes a purpose-built nonprivileged RBAC test identity.
- **Group model:** cloud security groups with assigned membership.

## Identity management

Fictional employees were provisioned with departmental/job metadata to simulate joiner/mover/leaver identity processes. A dedicated test user was created for testing administrative restrictions and later account offboarding.

## Security groups

Created five departmental groups:

| Group | Intended department |
|---|---|
| `BT-IT-Users` | IT |
| `BT-Security-Users` | Security |
| `BT-HR-Users` | Human Resources |
| `BT-Finance-Users` | Finance |
| `BT-Engineering-Users` | Engineering |

**Membership evidence:** `BT-Security-Users` showed **four** direct users: David Collins, Emily Foster, Michael Reed, and Sophia Bennett. Group overview showed zero owners; consider named owner governance in a subsequent assessment.

**Important:** Groups were created and memberships were validated; this does **not** prove application/resource permissions were granted through those groups.

## Role management and least privilege

1. Assigned built-in `User Administrator` to David Collins during the role exploration.
2. Reviewed intended job responsibilities (read-only IAM analyst access).
3. Removed `User Administrator` and granted built-in `Directory Readers`.
4. Verified the final role view showed a direct, built-in Directory Readers assignment.
5. Signed in as David in a separate browser session, opened the dedicated test user's directory details, and verified visibility of identity information while **Edit properties** and **Reset password** were unavailable.

The test supports read-only behavior for the specific management actions observed, not an exhaustive proof of all effective entitlements.

## Account lifecycle and sign-in sessions

A dedicated **RBAC test user** was disabled; after refresh the account overview displayed **Disabled**. A lab administrator initiated **Revoke sessions**, and Azure displayed successful revocation. The audit view showed successful **Update StsRefreshTokenValidFrom** activity. These are administrative action and audit-evidence observations; they do not guarantee instantaneous expiration of every access token and application session.

## Authentication inspection

For David Collins, the authentication methods page showed:

- Default sign-in method: Microsoft Authenticator notification.
- Registered Microsoft Authenticator on an iPhone.
- Registered passkey using Windows Hello.
- System-preferred MFA shown enabled with FIDO2 as preferred method.

The **evaluated Authentication methods policy (Preview)** for that user showed:

| Method | Observed status |
|---|---|
| FIDO2 security key | Enabled |
| Microsoft Authenticator | Enabled |
| SMS | Disabled |
| Temporary Access Pass | Enabled |
| Hardware OATH | Disabled |
| Software OATH | Enabled |
| Voice call | Disabled |
| Password | Enabled |
| Email OTP | Enabled |
| Certificate-based authentication | Disabled |

**Caution:** These statuses are from an evaluation for one user and do not establish effective tenant-wide MFA enforcement. Method registration alone does not show whether an MFA challenge occurred during every sign-in.

## Audit logging

Audited role-management and user-management events, including a successful role-member removal event, account disablement, and refresh-token-valid-from update. Reviewers should use corresponding screenshot rows and timestamps as bounded evidence of actions. Role-change targets must be inspected when attributing events to specific identities/roles.

## Responsible-use statement

This is an educational simulation. It did not access or modify any real employer's production directory. Avoid publishing tenant IDs, full UPNs, session IDs, authenticator details, usernames associated with real users, or unredacted administrative screenshots.
