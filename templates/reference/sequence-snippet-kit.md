---
tags: [architecture, diagram, reference, sequence, mermaid]
project: diagram-king
created: 2026-03-16
---

# Sequence Diagram — Snippet Kit

> [!info] Context
> Copy-paste snippets for enhancing Mermaid sequence diagrams. Drop these blocks into any sequence diagram to add conditionals, loops, annotations, and highlighted sections.

## Conditional Branch

Use `alt`/`else` for if/else logic in a sequence:

```mermaid
sequenceDiagram
    alt Token valid
        GW->>SVC: Forward request
    else Token expired
        GW-->>FE: 401 Unauthorized
    end
```

## Retry Loop

Use `loop` for repeated attempts:

```mermaid
sequenceDiagram
    loop Retry (max 3)
        SVC->>EXT: Call external API
    end
```

## Annotation

Use `Note` to add context to a participant:

```mermaid
sequenceDiagram
    Note over SVC: Business logic / validation here
```

## Highlighted Section

Use `rect` to visually group critical operations:

```mermaid
sequenceDiagram
    rect rgb(30, 50, 30)
        SVC->>DB: Critical transaction
        DB-->>SVC: Commit
    end
```
