# Security Review and Remediation Roadmap

## Observed strengths

- A dedicated test identity enabled repeatable nonprivileged lifecycle testing.
- Built-in User Administrator was replaced with Directory Readers when the analyst only needed to inspect records.
- Actual restricted controls were inspected in the analyst's separate session.
- Disablement, revocation and audit review were performed.
- Phishing-resistant passkeys and evaluated authentication policies were reviewed.

## Findings and recommendations

| Priority | Finding / limitation | Recommended next action | Project status |
|---|---|---|---|
| High | MFA enforcement was not verified for all users and apps | Review policies/licensing, sign-in logs and challenge outcomes | Not demonstrated |
| High | Effective privileges outside tested directory actions were not inventoried | Audit Azure RBAC, app assignments, group grants and inherited privileges | Not demonstrated |
| High | Existing access token and app-session termination not independently measured | Use authorized test app and sign-in logs to validate access termination behavior | Not demonstrated |
| Medium | Security group had no listed owners | Designate responsible owner(s), implement periodic membership recertification | Observed |
| Medium | No conditional or risk-based sign-in protections demonstrated | Evaluate Conditional Access and licensing; use suitable phishing-resistant policies | Future work |
| Medium | Privileged roles not managed through just-in-time activation | Evaluate PIM and eligible role assignment where licensed | Future work |
| Medium | Audit retention/export strategy not documented | Establish retention policy and secure log export procedure | Future work |
| Low | Manual screenshots and testing | Convert lab assertions into repeatable scripted checks with least-privileged Microsoft Graph access | Future work |

## Threat scenarios considered

**Phished password:** An attacker steals a password; prefer FIDO2 phishing-resistant authentication and limit privilege.

**Privilege accumulation on job transfer:** Employee moves from Security to Finance; review approved business need, remove obsolete group and role access, assign only necessary new permissions, document change.

**Departing employee:** Disable identity and revoke sessions; explicitly account for unexpired application access tokens.

**Unauthorized directory edits:** Limit modification roles; validate read-only behavior with the actual delegated identity; inspect audit trail.

## Evidence security

This repository is public. Never commit passwords, recovery methods, full personal UPNs, live tokens, session cookies, sensitive tenant/account identifiers, or unredacted screenshots. Keep raw screenshots local. Redact or crop, then inspect the final image before commit.

## Training vs. production

The project is a fictional hands-on training environment. Do not represent the lab as a real production deployment, regulatory compliance certification, or complete enforcement across all identities.
