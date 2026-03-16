---
tags: [architecture, diagram, d2, clean-architecture]
project: <ProjectName>
created: <date>
---

# Clean Architecture — D2

> [!info] Context
> A Clean Architecture system diagram using D2 with auto-layout. Shows client, API, core, and infrastructure layers with typed shapes.

## Diagram

```d2
direction: down

Client: {
  label: "Client Layer"
  style.fill: "#1e3a5f"
  style.stroke: "#4a9eff"

  Web: Angular App {shape: oval}
  Mobile: Mobile Client {shape: oval}
}

API: {
  label: "API Layer"
  style.fill: "#1a3a2a"
  style.stroke: "#4aff91"

  GW: API Gateway
  Auth: Auth Service
  Svc: Domain Service
}

Core: {
  label: "Application Core"
  style.fill: "#3a2a1a"
  style.stroke: "#ffaa4a"

  UC: Use Cases
  Domain: Domain Entities
  Ports: Ports & Interfaces {shape: hexagon}
}

Infra: {
  label: "Infrastructure"
  style.fill: "#2a1a3a"
  style.stroke: "#cc4aff"

  DB: PostgreSQL {shape: cylinder}
  Cache: Redis {shape: cylinder}
  Queue: Message Queue {shape: queue}
  Ext: External API {shape: cloud}
}

Client.Web -> API.GW
Client.Mobile -> API.GW
API.GW -> API.Auth
API.GW -> API.Svc
API.Svc -> Core.UC
Core.UC -> Core.Domain
Core.UC -> Core.Ports
Core.Ports -> Infra.DB
Core.Ports -> Infra.Cache
Core.Ports -> Infra.Queue
Core.Ports -> Infra.Ext
```

## Notes

- Requires the `d2-obsidian` plugin
- D2 auto-layout keeps nested subgraphs readable as they grow
- Customize node names, add/remove layers and services
