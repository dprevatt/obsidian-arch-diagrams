---
tags: [architecture, diagram, index]
---

# Architecture Diagram Templates

> [!info] About
> A library of starter templates for architecture diagrams in Obsidian. Browse by category below, pick a template, and customize it for your project.

## System Design

- [[system-design/system-overview-flowchart|System Overview Flowchart]] — Layered architecture, Clean Architecture style (Mermaid)
- [[system-design/clean-architecture-d2|Clean Architecture — D2]] — Clean Architecture system diagram with auto-layout (D2)
- [[system-design/c4-context-diagram|C4 Context Diagram]] — System boundary, actors, and external systems (D2)
- [[system-design/c4-container-diagram|C4 Container Diagram]] — Internal containers, drill-down from context (D2)

## Data Modeling

- [[data-modeling/domain-model-class-diagram|Domain Model — Class Diagram]] — Entities, aggregates, enums for DDD / Clean Architecture (Mermaid)
- [[data-modeling/database-erd|Database ERD]] — Table-level schema with PKs, FKs, and types (Mermaid)

## Infrastructure

- [[infrastructure/homelab-infrastructure|Homelab Infrastructure]] — Proxmox host, VMs, LXC containers, storage (D2)
- [[infrastructure/network-topology-d2|Network Topology]] — VLANs, routing, and device placement (D2)

## Integration

- [[integration/event-pipeline-flowchart|Event / Integration Pipeline]] — n8n, webhooks, automation flows (Mermaid)
- [[integration/request-lifecycle-sequence|Request Lifecycle — Sequence Diagram]] — HTTP request through a layered API (Mermaid)
- [[integration/webhook-async-sequence|Webhook / Async Flow — Sequence Diagram]] — Event publishing, background workers, retry logic (Mermaid)
- [[integration/state-diagram|State Diagram]] — Workflow state machines, order lifecycles (Mermaid)

## Reference

- [[reference/shape-reference|Shape Reference]] — Mermaid and D2 node shape syntax
- [[reference/color-palette|Color Palette — Dark Mode]] — Consistent color palette for all templates
- [[reference/sequence-snippet-kit|Sequence Diagram — Snippet Kit]] — Conditionals, loops, annotations, highlights

## Starters

- [[starters/blank-mermaid|Blank Mermaid Starter]] — Minimal flowchart with palette applied
- [[starters/blank-d2|Blank D2 Starter]] — Minimal D2 diagram with palette applied

---

## Tools

| Tool | Best For | Obsidian Support |
|------|----------|-----------------|
| **Mermaid** | Sequence, ERD, class diagrams, flowcharts | Native (built-in) |
| **D2** | System architecture, infrastructure, C4 | Plugin required (`d2-obsidian`) |
