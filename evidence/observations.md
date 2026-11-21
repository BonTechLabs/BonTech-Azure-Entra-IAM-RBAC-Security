# Evidence Observation Notes

These observations were recorded during the guided lab from screenshots submitted in the conversation. **The actual redacted image files are not yet present in the GitHub repository**. See [evidence inventory](README.md) for the expected filenames and redaction instructions.

| ID | Screenshot screen | Directly observed | Interpretation / constraint |
|---|---|---|---|
| E01 | Groups → All groups | Five department groups; each marked Security and Assigned | Confirms group configuration, not group-to-resource grants |
| E02 | BT-Security-Users → Members | Four direct user members: David Collins, Emily Foster, Michael Reed, Sophia Bennett | Validates membership list, not all employees’ job titles or entitlements |
| E03 | David Collins → Assigned roles | Built-in Directory Readers, direct assignment | Other role grants outside displayed view not exhaustively audited |
| E04 | David's separate browser session → test identity | Edit properties and Reset password greyed out; password-reset privilege notice | Confirms denied edit/reset functionality in the tested UI context |
| E05 | Test user → Overview | Account status Disabled | Confirms account state, not a tested failed sign-in event |
| E06 | User overview → Notifications | Successfully revoked sign-in sessions | Success of administrative action, not immediate termination of all app access |
| E07 | Test user → Audit logs | Successful Disable account and Update StsRefreshTokenValidFrom events | Corresponding administrative operation was logged |
| E08 | David → Authentication methods | Authenticator registered; Windows Hello passkey registered; system preferred FIDO2 shown | Registration does not prove MFA is forced on every sign-in |
| E09 | David → Evaluated Authentication methods policy | FIDO2 enabled, Microsoft Authenticator enabled, SMS disabled, voice call disabled | Applies to the evaluated user view, not entire tenant |

## Recommended evidence captions

- **E01:** Five departmental security groups provisioned using Assigned membership.
- **E02:** Four direct members validated in Security department group.
- **E03:** IAM analyst granted Directory Readers rather than broader User Administrator.
- **E04:** Effective access validation: account readable, administrative modification controls unavailable.
- **E05:** Dedicated test identity in Disabled state for offboarding simulation.
- **E06:** Administrative session revocation received a success notification.
- **E07:** Audit event shows corresponding token-valid-from update and account lifecycle actions.
- **E08:** Microsoft Authenticator and Windows Hello passkey registration observed for one analyst.
- **E09:** Evaluated methods policy shows phishing-resistant method enabled and SMS disabled for one user.

**Accuracy and privacy:** This is a simulated lab. Evidence rows are human-reviewed observations, not independent compliance attestation. Redact UPNs, tenant domains, identifiers and browser-session details before publication.
