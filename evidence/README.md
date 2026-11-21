# Evidence Register — Screenshots Pending Security Review

**Status:** The guided project included original screenshots, but **no raw screenshots are published here** because the source images display browser profiles, full account identifiers and other data not appropriate for a public portfolio.

Publish only manually inspected, redacted versions in this directory. Filename suggestions below deliberately do not assert files already exist.

| Evidence ID | Suggested filename | What must be visible | Supporting validation |
|---|---|---|---|
| E01 | `E01-department-groups-redacted.png` | Five Security groups and Assigned membership | T01 |
| E02 | `E02-security-group-members-redacted.png` | `BT-Security-Users` and four direct members | T02 |
| E03 | `E03-directory-readers-role-redacted.png` | David Collins's Directory Readers assignment (redact identity details as needed) | T03 |
| E04 | `E04-read-only-controls-redacted.png` | Analyst session and disabled Edit / Reset password UI | T04 |
| E05 | `E05-disabled-test-account-redacted.png` | Test identity's Disabled status | T05 |
| E06 | `E06-revoke-sessions-success-redacted.png` | Revocation-success notification | T06 |
| E07 | `E07-session-audit-redacted.png` | Successful token-valid-from audit row and timestamp | T07 |
| E08 | `E08-registered-methods-redacted.png` | Authenticator and passkey registration | T08 |
| E09 | `E09-evaluated-methods-redacted.png` | FIDO2 enabled / SMS disabled in David's evaluated policy | T09 |

## Redaction checklist

- Remove/cover full email addresses, login identifiers and complete tenant domain.
- Remove/cover GUID object IDs, tenant IDs, subscription IDs and any session/correlation IDs.
- Crop browser URL, unrelated tabs, signed-in avatar, notifications and machine desktop details.
- Never publish passwords, temporary access passes, MFA QR codes, recovery keys, passkeys or token material.
- Keep UI labels and the **specific positive/negative test result** readable.
- Review each **final flattened image** for residual information (including reflections, taskbar popups and tooltip contents).
- Do not equate a screenshot of configuration with proof of a tenant-wide policy or production-ready system.

## Evidence record template

```text
Evidence ID:
Security objective:
Test identity (fictional label only):
Expected result:
Observed result:
Timestamp (approximate):
Screenshot file:
Redaction performed:
Limitations / interpretation:
```

When screenshots are approved and committed, replace the pending entries with relative image links.
