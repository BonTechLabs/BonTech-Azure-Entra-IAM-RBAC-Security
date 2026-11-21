# BonTech Entra ID — Logical Security Architecture

The diagram below represents identity and security controls **observed in the training tenant**. It is not an Azure network architecture or a deployed application topology.

```mermaid
flowchart TB
    A["BonTech Consulting<br/>Microsoft Entra tenant<br/>(fictional lab)"]
    A --> B["Employee identities<br/>22 reported, incl. test user"]
    A --> C["Assigned security groups<br/>IT · Security · HR · Finance · Engineering"]
    A --> D["Directory role assignments"]
    A --> E["Authentication methods<br/>evaluated for David Collins"]
    A --> F["Entra audit logs"]
    C --> C1["BT-Security-Users<br/>4 direct users observed"]
    D --> D1["Global Administrator<br/>lab administrator"]
    D --> D2["Directory Readers<br/>David Collins"]
    D2 --> G["Separate-session access test<br/>read allowed; edit/reset disabled"]
    E --> E1["Authenticator + Windows Hello passkey registered"]
    E --> E2["FIDO2 enabled / SMS disabled<br/>in user's evaluated methods policy"]
    B --> H["RBAC test user"]
    H --> I["Account disabled"]
    H --> J["Sign-in sessions revoked"]
    I --> F
    J --> F
    G --> F
```

## Trust boundaries

| Boundary | Engineering implication |
|---|---|
| Tenant vs. Azure subscription | The directory controls identities; subscription/resource authorization is separately assigned. |
| Users vs. security groups | Membership organizes users but does not itself grant application permissions. |
| Directory role vs. effective access | The existence of an assignment requires direct validation under that identity. |
| Authentication method vs. MFA enforcement | Method registration and eligibility do not prove that every sign-in enforces MFA. |
| Administrative operation vs. active session | Disabling and revoking refresh sessions reduce continued access; existing access tokens can persist. |

## Scope explicitly not shown

No virtual network, application deployment, automated identity provisioning pipeline, custom Microsoft Graph automation, Conditional Access policy, PIM workflow, or tenant-wide MFA test was demonstrated in the guided project. Do not infer these from the diagram.
