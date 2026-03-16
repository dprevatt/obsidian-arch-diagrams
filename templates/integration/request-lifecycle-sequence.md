---
tags: [architecture, diagram, sequence, mermaid, api, request]
project: <ProjectName>
created: <date>
---

# Request Lifecycle — Sequence Diagram

> [!info] Context
> A standard HTTP request flow through a layered API showing authentication, domain logic, and database interaction. Swap actor and participant names to match your stack.

## Diagram

```mermaid
sequenceDiagram
    autonumber
    actor User
    participant FE as Frontend
    participant GW as API Gateway
    participant AUTH as Auth Service
    participant SVC as Domain Service
    participant DB as Database

    User->>FE: Action / interaction
    FE->>GW: HTTP request + JWT

    GW->>AUTH: Validate token
    AUTH-->>GW: Valid

    GW->>SVC: Forward request
    activate SVC

    SVC->>DB: Query or command
    DB-->>SVC: Result set

    SVC-->>GW: Response DTO
    deactivate SVC

    GW-->>FE: 200 OK + payload
    FE-->>User: Updated UI
```

## Notes

- Swap participant names (FE, GW, AUTH, SVC, DB) to match your services
- Add `alt`/`else` blocks for error paths
- Add `loop` blocks for retry logic
- See [[reference/sequence-snippet-kit|Sequence Snippet Kit]] for more patterns
