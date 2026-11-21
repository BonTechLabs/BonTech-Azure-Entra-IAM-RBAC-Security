# Engineering Decision Record

## ADR-001 — Read-only directory role for IAM analyst

**Context:** The simulated IAM analyst must inspect employee directory data but does not require account creation, edits or password resets.

**Decision:** Replace the built-in `User Administrator` role with `Directory Readers`.

**Why:** Restricts modification capability and reduces privilege misuse or accidental changes while preserving needed directory visibility.

**Validation:** Final directory role assignment viewed; separate analyst browser session could see the test identity but edit/reset controls were unavailable.

**Residual risk:** Read-only access still exposes directory information; role permissions are not a complete assessment of app/resource entitlements.

## ADR-002 — Departmental group model

**Context:** Fictional organization with IT, Security, HR, Finance and Engineering teams.

**Decision:** Use five security groups with assigned membership.

**Why:** Simplifies membership governance and supports consistent role- or application-based authorization *when resource permissions are attached separately*.

**Validation:** All five groups seen in list; Security group contained four direct members.

**Residual risk:** No named owners observed for Security group; no resource permission bindings demonstrated.

## ADR-003 — Disable plus revoke on employee departure

**Decision:** For the nonprivileged lab test identity, disable the account and revoke sign-in sessions.

**Why:** Disabling blocks normal new authentication; revocation invalidates refresh tokens and certain persistent sign-in sessions.

**Validation:** Disabled status, revocation success notification and relevant audit activity were observed.

**Residual risk:** Already issued access tokens and app sessions can remain usable depending on expiry and app enforcement; no end-to-end application sign-out test performed.

## ADR-004 — Prefer phishing-resistant authentication

**Context:** An evaluated policy and registered methods were reviewed for the IAM analyst.

**Observation:** Microsoft Authenticator, Windows Hello passkey and FIDO2 eligibility were shown; SMS and voice call were disabled in the individual's evaluated policy.

**Security rationale:** FIDO2 uses origin-bound public-key credentials and resists fake-site credential phishing in ways that shared codes do not.

**Validation boundary:** Inspected methods and evaluated settings only. No tenant-wide or per-application mandatory phishing-resistant authentication policy was proven.
