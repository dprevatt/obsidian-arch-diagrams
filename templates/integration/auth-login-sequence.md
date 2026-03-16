---
tags: [architecture, diagram, sequence, mermaid, auth, oauth]
project: <ProjectName>
created: 2026-03-16
---

# Auth / Login Flow — Sequence Diagram

> [!info] Context
> An OAuth2/OIDC authorization code flow with token refresh. Use for documenting authentication flows, SSO integrations, or API authorization patterns.

## Diagram

```mermaid
sequenceDiagram
    autonumber
    actor User
    participant SPA as Frontend
    participant API as Backend
    participant IdP as Identity Provider

    User->>SPA: Click Login
    SPA->>IdP: Redirect to /authorize
    User->>IdP: Authenticate (credentials / MFA)
    IdP->>SPA: Redirect with authorization code
    SPA->>API: POST /auth/callback (code)
    API->>IdP: POST /token (code + client_secret)
    IdP-->>API: access_token + refresh_token
    API->>API: Store refresh_token (secure storage)
    API-->>SPA: access_token + session cookie
    SPA->>SPA: Store access_token (memory)

    alt Token expired
        SPA->>API: GET /resource (expired token)
        API-->>SPA: 401 Unauthorized
        SPA->>API: POST /auth/refresh
        API->>IdP: POST /token (refresh_token)
        IdP-->>API: New access_token
        API-->>SPA: New access_token
    end
```

## Notes

- Swap IdP name to match your provider (Auth0, Okta, Keycloak, etc.)
- Add `Note over` blocks to annotate security considerations
- See [[reference/sequence-snippet-kit|Sequence Snippet Kit]] for more patterns
