---
tags: [architecture, diagram, flowchart, mermaid, etl, data]
project: <ProjectName>
created: 2026-03-16
---

# ETL / Data Flow Pipeline

> [!info] Context
> An ETL (Extract, Transform, Load) pipeline showing data movement from source systems through processing to a data warehouse. Use for documenting data engineering pipelines, analytics workflows, or data migration flows.

## Diagram

```mermaid
flowchart LR
    subgraph Sources["Sources"]
        PDB[(Production DB)]
        RAPI{{REST API}}
        CSV[CSV / Files]
        EVT>Event Stream]
    end

    subgraph Extract["Extract"]
        DBC[DB Connector]
        APC[API Poller]
        FLR[File Reader]
        SCN[Stream Consumer]
    end

    subgraph Transform["Transform"]
        VAL[Validate]
        CLN[Clean]
        ENR[Enrich]
        AGG[Aggregate]
    end

    subgraph Load["Load"]
        DWH[(Data Warehouse)]
        DLK[(Data Lake)]
        ADB[(Analytics DB)]
    end

    subgraph Serve["Serve"]
        DSH[Dashboard]
        RPT[Reports]
        MLP[ML Pipeline]
    end

    PDB --> DBC
    RAPI --> APC
    CSV --> FLR
    EVT --> SCN

    DBC --> VAL
    APC --> VAL
    FLR --> VAL
    SCN --> VAL

    VAL --> CLN
    CLN --> ENR
    ENR --> AGG

    AGG --> DWH
    AGG --> DLK
    AGG --> ADB

    DWH --> DSH
    DLK --> MLP
    ADB --> RPT

    style Sources fill:#2e1a1a,stroke:#ff4a4a,color:#ffe0e0
    style Extract fill:#1e3a5f,stroke:#4a9eff,color:#e0f0ff
    style Transform fill:#3a2a1a,stroke:#ffaa4a,color:#fff5e0
    style Load fill:#1a3a2a,stroke:#4aff91,color:#e0ffe8
    style Serve fill:#2a1a3a,stroke:#cc4aff,color:#f5e0ff
```

## Notes

- Add/remove sources and destinations as needed
- Add error handling paths (dead letter queues, retry logic)
- Customize transformation steps for your pipeline
- Add scheduling annotations for batch vs streaming
