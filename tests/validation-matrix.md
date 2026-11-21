# Security Test Matrix

Legend: **PASS** = a specific observable assertion succeeded; **PARTIAL** = evidence does not validate entire control; **NOT VERIFIED** = not tested.

| ID | Security objective | Evidence observed | Outcome | Limitation |
|---|---|---|---|---|
| T01 | Department groups exist | Five Security groups with Assigned membership in portal | PASS | No automated drift check |
| T02 | Security group membership | Four direct members listed in `BT-Security-Users` | PASS | Other departments not exhaustively reviewed |
| T03 | Read-only Entra role | David Collins: Directory Readers direct built-in role; User Administrator not shown | PASS | Other entitlements not exhaustively inventoried |
| T04 | Effective restriction | Separate David session showed Edit properties and Reset password disabled | PASS | Only tested actions established |
| T05 | Disable identity | Test account overview showed Disabled | PASS | No independent blocked sign-in attempt collected |
| T06 | Revoke sessions | Portal displayed successful sign-in session revocation | PASS | No application-wide immediate sign-out proof |
| T07 | Audit of lifecycle actions | Successful Disable account / `Update StsRefreshTokenValidFrom` events seen | PASS | Administrative action evidence, not token expiry proof |
| T08 | Authentication methods | David: Microsoft Authenticator and Windows Hello passkey registered | PASS | Registration != enforcement |
| T09 | Evaluated method policy | FIDO2 enabled and SMS disabled for David in evaluated policy | PASS | Not a tenant-wide compliance evaluation |
| T10 | MFA enforced on every sign-in | No complete sign-in and Conditional Access evidence | NOT VERIFIED | Requires additional testing/licensing as applicable |
| T11 | Least privilege across all Azure resources | Not tested | NOT VERIFIED | Requires full resource/app entitlement audit |
| T12 | Recovery and privileged account controls | Not tested | NOT VERIFIED | Require documented break-glass and access review |

## Evidence acceptance criteria

Each published screenshot should display the **relevant UI state** while redacting the account avatar/name, email/UPN, tenant domain, object IDs, browser profile identifiers and unrelated tabs. Record the date, operation, expected result, observed result, and whether the screenshot is redacted.

Do not claim a tenant-wide result from one-user policy views or attribute a role-change event to a named role until target detail is independently inspected.
