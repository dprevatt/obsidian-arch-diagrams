---
tags: [architecture, diagram, reference, color]
project: diagram-king
created: 2026-03-16
---

# Color Palette — Dark Mode

> [!info] Context
> The dark-mode color palette used across all templates. Optimized for Obsidian's dark theme. Reference this when creating new diagrams or customizing existing templates.

## Palette

| Layer              | Fill      | Stroke    | Text      |
|--------------------|-----------|-----------|-----------|
| Client / UI        | `#1e3a5f` | `#4a9eff` | `#e0f0ff` |
| API / Gateway      | `#1a3a2a` | `#4aff91` | `#e0ffe8` |
| Domain / Core      | `#3a2a1a` | `#ffaa4a` | `#fff5e0` |
| Infrastructure     | `#2a1a3a` | `#cc4aff` | `#f5e0ff` |
| External Systems   | `#2e1a1a` | `#ff4a4a` | `#ffe0e0` |
| Storage / Data     | `#2e1e1a` | `#ff7044` | `#ffe8e0` |
| Automation / Jobs  | `#1a1e2e` | `#66aaff` | `#e0eeff` |
| System Boundary    | `#0f1f2f` | `#3399ff` | `#cce4ff` |

## Usage

### Mermaid

```
style SubgraphName fill:#1e3a5f,stroke:#4a9eff,color:#e0f0ff
```

### D2

```
Container: {
  style.fill: "#1e3a5f"
  style.stroke: "#4a9eff"
}
```
