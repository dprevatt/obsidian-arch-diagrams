---
tags: [architecture, diagram, d2, c4, container]
project: <ProjectName>
created: <date>
---

# C4 Container Diagram

> [!info] Context
> A C4 Container-level diagram showing internal containers within a system boundary. Drill down from the [[system-design/c4-context-diagram|C4 Context Diagram]] to see what's inside your system.

## Diagram

```d2
direction: down

vars: {
  d2-config: {
    layout-engine: elk
  }
}

boundary: {
  label: "Your System"
  style.stroke-dash: 5
  style.fill: "#0a0f1a"
  style.stroke: "#3399ff"

  spa: SPA / Frontend {
    shape: rectangle
    style.fill: "#1e3a5f"
    style.stroke: "#4a9eff"
  }

  api: API Application {
    shape: rectangle
    style.fill: "#1a3a2a"
    style.stroke: "#4aff91"
    label: "API Application\n.NET / Clean Architecture"
  }

  worker: Worker Service {
    shape: hexagon
    style.fill: "#2a1a3a"
    style.stroke: "#cc4aff"
    label: "Background Worker\nHosted Service"
  }

  db: Primary Database {
    shape: cylinder
    style.fill: "#2e1e1a"
    style.stroke: "#ff7044"
    label: "PostgreSQL\nvia EF Core"
  }

  cache: Cache {
    shape: cylinder
    style.fill: "#2e1e1a"
    style.stroke: "#ff7044"
    label: "Redis\nSession / Cache"
  }

  queue: Message Bus {
    shape: queue
    style.fill: "#1a1e2e"
    style.stroke: "#66aaff"
  }
}

user: User {shape: person}
ext: External Service {shape: cloud}

user -> boundary.spa: HTTPS
boundary.spa -> boundary.api: REST / JSON
boundary.api -> boundary.db: Reads / Writes
boundary.api -> boundary.cache: Cache ops
boundary.api -> boundary.queue: Publishes events
boundary.worker -> boundary.queue: Consumes events
boundary.worker -> ext: Calls
```

## Notes

- Requires the `d2-obsidian` plugin
- Uses ELK layout engine for cleaner auto-layout
- Related: [[system-design/c4-context-diagram|C4 Context Diagram]]
- Add/remove containers, change labels to match your tech stack
