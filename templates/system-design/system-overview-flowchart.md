---
tags: [architecture, diagram, flowchart, mermaid]
project: <ProjectName>
created: <date>
---

# System Overview Flowchart

> [!info] Context
> A layered system architecture diagram in Clean Architecture style. Shows client, API, core, and infrastructure layers with their relationships.

## Diagram

```mermaid
flowchart TD
    subgraph Client["Client Layer"]
        UI([Angular / Web App])
        MOB([Mobile Client])
    end

    subgraph API["API Layer"]
        GW[API Gateway]
        AUTH[Auth Service]
        SVC[Domain Service]
    end

    subgraph Core["Application Core"]
        UC[[Use Cases]]
        DOM[Domain Entities]
        IFACE[/Interfaces & Ports/]
    end

    subgraph Infra["Infrastructure"]
        DB[(PostgreSQL)]
        CACHE[(Redis)]
        QUEUE>Message Queue]
        EXT{{External API}}
    end

    UI --> GW
    MOB --> GW
    GW --> AUTH
    GW --> SVC
    SVC --> UC
    UC --> DOM
    UC --> IFACE
    IFACE --> DB
    IFACE --> CACHE
    IFACE --> QUEUE
    IFACE --> EXT

    style Client fill:#1e3a5f,stroke:#4a9eff,color:#e0f0ff
    style API fill:#1a3a2a,stroke:#4aff91,color:#e0ffe8
    style Core fill:#3a2a1a,stroke:#ffaa4a,color:#fff5e0
    style Infra fill:#2a1a3a,stroke:#cc4aff,color:#f5e0ff
```

## Notes

- Blue — Client / Presentation
- Green — API / Application
- Amber — Domain / Core
- Purple — Infrastructure / Data
- Swap node names and add/remove layers to match your system
