---
tags: [architecture, diagram, reference]
project: diagram-king
created: 2026-03-16
---

# Shape Reference

> [!info] Context
> Quick-reference for node shapes in both Mermaid and D2. Use when building diagrams to pick the right shape for each component type.

## Mermaid Shapes

| Component Type     | Syntax          | Renders As        |
|--------------------|-----------------|-------------------|
| Service / Box      | `[Name]`        | Rectangle         |
| Database           | `[(Name)]`      | Cylinder          |
| External System    | `{{Name}}`      | Hexagon           |
| User / Actor       | `([Name])`      | Stadium / Pill    |
| Queue              | `>Name]`        | Asymmetric        |
| Decision           | `{Name}`        | Diamond           |
| Process / Worker   | `[[Name]]`      | Subroutine box    |
| Cloud / Infra      | `[/Name/]`      | Parallelogram     |

## D2 Shapes

| Component Type     | D2 Shape         |
|--------------------|------------------|
| Database           | `shape: cylinder`|
| External / Cloud   | `shape: cloud`   |
| Queue              | `shape: queue`   |
| Person / Actor     | `shape: person`  |
| Decision           | `shape: diamond` |
| Process            | `shape: hexagon` |
