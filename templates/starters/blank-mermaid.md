---
tags: [architecture, diagram, mermaid, starter]
project: <ProjectName>
created: <date>
---

# Blank Mermaid Starter

> [!info] Context
> A minimal Mermaid flowchart with the project color palette applied. Replace the placeholder nodes and customize.

## Diagram

```mermaid
flowchart TD
    subgraph Layer1["Layer 1"]
        A[Node A]
        B[Node B]
    end

    subgraph Layer2["Layer 2"]
        C[Node C]
        D[Node D]
    end

    A --> C
    B --> D

    style Layer1 fill:#1e3a5f,stroke:#4a9eff,color:#e0f0ff
    style Layer2 fill:#1a3a2a,stroke:#4aff91,color:#e0ffe8
```

## Notes

- Rename subgraphs and nodes to match your system
- See [[reference/color-palette|Color Palette]] for all available colors
- See [[reference/shape-reference|Shape Reference]] for node shape syntax
