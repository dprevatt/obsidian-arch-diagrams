# Additional Templates — Design Spec

## Goal

Add 9 new diagram templates to the existing Obsidian architecture template library and update the index.

## Source

All new templates — none are extracted from CLAUDE.md. All follow the established note wrapper format, color palette, and folder conventions.

## New Files

### system-design/

- `microservices-communication-d2.md` — Service mesh showing sync (REST/gRPC) and async (event bus) communication between multiple services. D2.

### infrastructure/

- `docker-compose-stack-d2.md` — Docker Compose stack showing services, networks, volumes, and port mappings. D2.
- `threat-model-d2.md` — Trust boundaries, data flows, and threat zones for security modeling. D2.

### integration/

- `cicd-pipeline-flowchart.md` — Build, test, deploy pipeline with environment stages (dev/staging/prod). Mermaid flowchart LR.
- `auth-login-sequence.md` — OAuth2/OIDC login flow with token refresh. Mermaid sequence diagram.
- `etl-data-flow-flowchart.md` — Source systems, extraction, transformation, loading, data warehouse. Mermaid flowchart LR.

### planning/ (new folder)

- `mindmap.md` — Mermaid mindmap for brainstorming and knowledge organization.
- `gantt-chart.md` — Mermaid Gantt chart for project planning.
- `git-branching-strategy.md` — Mermaid gitgraph showing trunk-based or gitflow patterns.

## Modified Files

- `templates/index.md` — Add new `## Planning` section, add entries to existing System Design, Infrastructure, and Integration sections.

## File Format

Same as existing templates:

```markdown
---
tags: [architecture, diagram, <type-tags>]
project: <ProjectName>
created: <date>
---

# <Title>

> [!info] Context
> <Description>

## Diagram

```<mermaid or d2>
<code>
```

## Notes

- <Hints>
```

## Color Palette

Same dark-mode palette as all existing templates.

## Out of Scope

- No changes to existing templates
- No new reference files
