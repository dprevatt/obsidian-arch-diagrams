---
tags: [architecture, diagram, flowchart, mermaid, integration, pipeline]
project: <ProjectName>
created: <date>
---

# Event / Integration Pipeline

> [!info] Context
> An event-driven pipeline diagram for n8n workflows, webhooks, automation, or any integration flow. Direction is left-to-right since pipelines read naturally that way.

## Diagram

```mermaid
flowchart LR
    subgraph Triggers["Triggers"]
        WH{{Webhook}}
        CRON[[Scheduled Job]]
        EVT>Event / Message]
    end

    subgraph Process["Processing"]
        GATE{Filter / Gate}
        XFORM[[Transform]]
        ENRICH[[Enrich / Lookup]]
    end

    subgraph Outputs["Outputs"]
        API[/REST API Call/]
        DB[(Database Write)]
        NOTIFY([Notification])
        EXT{{External Service}}
    end

    WH --> GATE
    CRON --> GATE
    EVT --> GATE

    GATE -->|Pass| XFORM
    GATE -->|Reject| NOTIFY

    XFORM --> ENRICH
    ENRICH --> API
    ENRICH --> DB
    API --> EXT
    API --> NOTIFY

    style Triggers fill:#1a2a3a,stroke:#4a9eff,color:#e0f0ff
    style Process fill:#2a1a3a,stroke:#cc66ff,color:#f0e0ff
    style Outputs fill:#1a3a2a,stroke:#44ff88,color:#e0fff0
```

## Notes

- Add/remove triggers, processors, and outputs as needed
- Use edge labels (`-->|label|`) to annotate conditional paths
- Swap subgraph names to match your pipeline stages
