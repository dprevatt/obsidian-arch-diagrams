# Obsidian Architecture Diagram Templates — Design Spec

## Goal

Generate a folder structure of architecture diagram starter templates that can be dropped directly into any Obsidian vault. Users should be able to browse an index note, follow links to templates, and quickly customize diagrams for their own use.

## Source Material

All templates and reference material already exist in `CLAUDE.md`. This project extracts them into individual Obsidian-ready notes and adds three new templates (state diagram, network topology, blank starters).

## Folder Structure

```
templates/
├── index.md
├── system-design/
│   ├── system-overview-flowchart.md
│   ├── clean-architecture-d2.md
│   ├── c4-context-diagram.md
│   └── c4-container-diagram.md
├── data-modeling/
│   ├── domain-model-class-diagram.md
│   └── database-erd.md
├── infrastructure/
│   ├── homelab-infrastructure.md
│   └── network-topology-d2.md
├── integration/
│   ├── event-pipeline-flowchart.md
│   ├── request-lifecycle-sequence.md
│   ├── webhook-async-sequence.md
│   └── state-diagram.md
├── reference/
│   ├── shape-reference.md
│   ├── color-palette.md
│   └── sequence-snippet-kit.md
└── starters/
    ├── blank-mermaid.md
    └── blank-d2.md
```

## File Format

Every template file uses the Obsidian note wrapper:

```markdown
---
tags: [architecture, diagram, <type>]
project: <ProjectName>
created: <date>
---

# <Diagram Title>

> [!info] Context
> <What this diagram shows and why.>

## Diagram

```<mermaid or d2>
<diagram code>
```

## Notes

- <Key decisions or assumptions>
- <Customization hints>
```

## Index File

`templates/index.md` contains:

- Brief intro to the template library
- Sections matching the folder categories (System Design, Data Modeling, Infrastructure, Integration, Reference, Starters)
- Each entry is a wiki-link (`[[path/to/template]]`) with a one-line description
- Color palette summary and tool info (Mermaid vs D2)

## New Templates

### State Diagram (Mermaid)

- Located in `integration/state-diagram.md`
- Generic state machine template (e.g., order lifecycle or CI/CD pipeline)
- Uses the project's dark-mode color palette

### Network Topology (D2)

- Located in `infrastructure/network-topology-d2.md`
- Simpler than the homelab template — general-purpose network layout
- Nodes for router, switches, servers, clients
- Uses the project's dark-mode color palette

### Blank Starters

- `starters/blank-mermaid.md` — minimal Mermaid flowchart with color palette applied, ready to customize
- `starters/blank-d2.md` — minimal D2 diagram with color palette applied, ready to customize

## Existing Templates (extracted from CLAUDE.md)

Each is copied verbatim from CLAUDE.md, wrapped in the note wrapper:

1. System Overview Flowchart (Mermaid)
2. Event/Integration Pipeline Flowchart (Mermaid)
3. Request Lifecycle Sequence (Mermaid)
4. Webhook/Async Sequence (Mermaid)
5. Domain Model Class Diagram (Mermaid)
6. Database ERD (Mermaid)
7. Clean Architecture (D2)
8. Homelab Infrastructure (D2)
9. C4 Context Diagram (D2)
10. C4 Container Diagram (D2)

## Reference Files

- `reference/shape-reference.md` — Mermaid and D2 shape tables combined
- `reference/color-palette.md` — Full dark-mode palette table
- `reference/sequence-snippet-kit.md` — Conditionals, loops, annotations, highlights for sequence diagrams

## Color Palette

All templates use the consistent dark-mode palette from CLAUDE.md:

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

## Out of Scope

- No `.obsidian/` config — this is not a standalone vault, just a folder to add to one
- No light-mode palette variants (noted as future contribution in README)
- No automation or scripting — just static markdown files
