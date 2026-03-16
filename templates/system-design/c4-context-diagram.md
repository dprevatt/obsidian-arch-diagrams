---
tags: [architecture, diagram, d2, c4, context]
project: <ProjectName>
created: <date>
---

# C4 Context Diagram

> [!info] Context
> A C4 Context-level diagram showing system boundary, actors, and external systems. Use this as the highest-level view of your system.

## Diagram

```d2
direction: right

vars: {
  d2-config: {
    layout-engine: elk
  }
}

system: {
  label: "System Boundary"
  style.stroke-dash: 5
  style.fill: "#0f1f2f"
  style.stroke: "#3399ff"

  core: Core Application
  api: Public API
  worker: Background Workers {shape: hexagon}
}

user: End User {shape: person}
admin: Admin {shape: person}
auth_ext: Auth Provider {shape: cloud}
payments: Payment Provider {shape: cloud}
email: Email Service {shape: cloud}

user -> system.core: Uses via browser
admin -> system.core: Manages via dashboard
system.core -> auth_ext: Authenticates via
system.core -> payments: Charges via
system.worker -> email: Sends via
system.api -> user: Webhooks to
```

## Notes

- Requires the `d2-obsidian` plugin
- Uses ELK layout engine for cleaner auto-layout
- Add/remove actors (person shapes) and external systems (cloud shapes)
- Keep this diagram high-level — drill down in the Container diagram
