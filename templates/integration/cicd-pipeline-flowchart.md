---
tags: [architecture, diagram, flowchart, mermaid, cicd, pipeline]
project: <ProjectName>
created: 2026-03-16
---

# CI/CD Pipeline

> [!info] Context
> A CI/CD pipeline showing build, test, and deploy stages across environments. Use for documenting GitHub Actions, GitLab CI, Jenkins, or any deployment pipeline.

## Diagram

```mermaid
flowchart LR
    subgraph Source["Source"]
        GP[Git Push]
        PR[PR Created]
    end

    subgraph Build["Build"]
        ID[Install Deps]
        LN[Lint]
        CP[Compile]
        BI[Build Image]
    end

    subgraph Test["Test"]
        UT[Unit Tests]
        IT[Integration Tests]
        E2E[E2E Tests]
    end

    TP{Tests Pass?}
    NF[Notify Team]

    subgraph Deploy["Deploy"]
        DD[Deploy Dev]
        DS[Deploy Staging]
        AG{Approve?}
        DP[Deploy Prod]
    end

    GP --> PR
    PR --> ID
    ID --> LN
    LN --> CP
    CP --> BI
    BI --> UT
    UT --> IT
    IT --> E2E
    E2E --> TP
    TP -- Pass --> DD
    TP -- Fail --> NF
    DD --> DS
    DS --> AG
    AG -- Approved --> DP

    style Source fill:#1e3a5f,stroke:#4a9eff,color:#e0f0ff
    style Build fill:#3a2a1a,stroke:#ffaa4a,color:#fff5e0
    style Test fill:#2a1a3a,stroke:#cc4aff,color:#f5e0ff
    style Deploy fill:#1a3a2a,stroke:#4aff91,color:#e0ffe8
```

## Notes

- Add/remove stages to match your pipeline
- Add approval gates with decision diamonds
- Customize environment names (dev/staging/prod)
- Add parallel paths for independent test suites
