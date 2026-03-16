# Obsidian Architecture Diagram Templates — Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Extract all diagram templates from CLAUDE.md into individual Obsidian-ready notes in a browsable folder structure, and add three new templates (state diagram, network topology, blank starters).

**Architecture:** Static markdown files organized by use case. Each file uses the Obsidian note wrapper (frontmatter, callout, notes section). An index file provides wiki-link navigation across all templates.

**Tech Stack:** Markdown, Mermaid, D2

**Spec:** `docs/superpowers/specs/2026-03-16-obsidian-arch-templates-design.md`

**Source material:** `CLAUDE.md` (all existing templates and reference tables)

---

## Chunk 1: System Design Templates

### Task 1: Create system-design folder and System Overview Flowchart

**Files:**
- Create: `templates/system-design/system-overview-flowchart.md`

- [ ] **Step 1: Create directory structure**

```bash
mkdir -p templates/system-design
```

- [ ] **Step 2: Create system-overview-flowchart.md**

Extract the "Flowchart — System Overview" template from `CLAUDE.md:119-161`. Wrap in note wrapper with:
- tags: `[architecture, diagram, flowchart, mermaid]`
- Context callout explaining this is a layered architecture diagram (Clean Architecture style)
- Notes section with the layer color key and customization hints

- [ ] **Step 3: Commit**

```bash
git add templates/system-design/system-overview-flowchart.md
git commit -m "feat: add system overview flowchart template"
```

### Task 2: Create Clean Architecture D2 template

**Files:**
- Create: `templates/system-design/clean-architecture-d2.md`

- [ ] **Step 1: Create clean-architecture-d2.md**

Extract the "D2 — System Architecture (Clean Architecture)" template from `CLAUDE.md:451-505`. Wrap in note wrapper with:
- tags: `[architecture, diagram, d2, clean-architecture]`
- Context callout explaining this is a Clean Architecture system diagram with auto-layout
- Notes section mentioning D2 plugin requirement and customization hints

- [ ] **Step 2: Commit**

```bash
git add templates/system-design/clean-architecture-d2.md
git commit -m "feat: add clean architecture D2 template"
```

### Task 3: Create C4 Context Diagram

**Files:**
- Create: `templates/system-design/c4-context-diagram.md`

- [ ] **Step 1: Create c4-context-diagram.md**

Extract the "D2 — C4 Context Diagram" template from `CLAUDE.md:586-618`. Wrap in note wrapper with:
- tags: `[architecture, diagram, d2, c4, context]`
- Context callout explaining C4 context level — system boundary, actors, external systems
- Notes section with hints on adding/removing actors and external systems

- [ ] **Step 2: Commit**

```bash
git add templates/system-design/c4-context-diagram.md
git commit -m "feat: add C4 context diagram template"
```

### Task 4: Create C4 Container Diagram

**Files:**
- Create: `templates/system-design/c4-container-diagram.md`

- [ ] **Step 1: Create c4-container-diagram.md**

Extract the "D2 — C4 Container Diagram" template from `CLAUDE.md:626-692`. Wrap in note wrapper with:
- tags: `[architecture, diagram, d2, c4, container]`
- Context callout explaining this is a drill-down from the C4 Context diagram showing internal containers
- Notes section with link to C4 context diagram and customization hints

- [ ] **Step 2: Commit**

```bash
git add templates/system-design/c4-container-diagram.md
git commit -m "feat: add C4 container diagram template"
```

---

## Chunk 2: Data Modeling Templates

### Task 5: Create Domain Model Class Diagram

**Files:**
- Create: `templates/data-modeling/domain-model-class-diagram.md`

- [ ] **Step 1: Create directory and file**

```bash
mkdir -p templates/data-modeling
```

Extract the "Class Diagram — Domain Model" template from `CLAUDE.md:317-380`. Wrap in note wrapper with:
- tags: `[architecture, diagram, class-diagram, mermaid, domain-model]`
- Context callout explaining this is for Clean Architecture domain layers, EF Core models, or any OOP structure
- Notes section with hints on adding/removing entities, relationships, and enums

- [ ] **Step 2: Commit**

```bash
git add templates/data-modeling/domain-model-class-diagram.md
git commit -m "feat: add domain model class diagram template"
```

### Task 6: Create Database ERD

**Files:**
- Create: `templates/data-modeling/database-erd.md`

- [ ] **Step 1: Create database-erd.md**

Extract the "ERD — Database Schema" template from `CLAUDE.md:389-440`. Wrap in note wrapper with:
- tags: `[architecture, diagram, erd, mermaid, database]`
- Context callout explaining this is for database design, EF Core schema review, or data modeling
- Notes section with hints on adding tables, columns, and relationship types

- [ ] **Step 2: Commit**

```bash
git add templates/data-modeling/database-erd.md
git commit -m "feat: add database ERD template"
```

---

## Chunk 3: Infrastructure Templates

### Task 7: Create Homelab Infrastructure template

**Files:**
- Create: `templates/infrastructure/homelab-infrastructure.md`

- [ ] **Step 1: Create directory and file**

```bash
mkdir -p templates/infrastructure
```

Extract the "D2 — Infrastructure / Homelab" template from `CLAUDE.md:511-580`. Wrap in note wrapper with:
- tags: `[architecture, diagram, d2, infrastructure, homelab, proxmox]`
- Context callout explaining this is for Proxmox homelab layouts with VMs, LXC containers, and storage
- Notes section with D2 plugin requirement and hints on adding/removing VMs and containers

- [ ] **Step 2: Commit**

```bash
git add templates/infrastructure/homelab-infrastructure.md
git commit -m "feat: add homelab infrastructure D2 template"
```

### Task 8: Create Network Topology D2 template (NEW)

**Files:**
- Create: `templates/infrastructure/network-topology-d2.md`

- [ ] **Step 1: Create network-topology-d2.md**

This is a NEW template (not in CLAUDE.md). Create a general-purpose network topology diagram using D2 with:
- Nodes: Internet, Firewall/Router, Core Switch, Access Switches, Server VLAN (web server, app server, DB server), Client VLAN (workstations), Management VLAN (monitoring, admin)
- Uses the project's dark-mode color palette
- tags: `[architecture, diagram, d2, infrastructure, network]`
- Context callout explaining this is a general-purpose network topology diagram
- Notes section with hints on adding VLANs, devices, and connections

- [ ] **Step 2: Commit**

```bash
git add templates/infrastructure/network-topology-d2.md
git commit -m "feat: add network topology D2 template"
```

---

## Chunk 4: Integration Templates

### Task 9: Create Event Pipeline Flowchart

**Files:**
- Create: `templates/integration/event-pipeline-flowchart.md`

- [ ] **Step 1: Create directory and file**

```bash
mkdir -p templates/integration
```

Extract the "Flowchart — Event / Integration Pipeline" template from `CLAUDE.md:177-214`. Wrap in note wrapper with:
- tags: `[architecture, diagram, flowchart, mermaid, integration, pipeline]`
- Context callout explaining this is for n8n workflows, webhooks, automation, or event-driven flows
- Notes section with hints on adding triggers, processors, and outputs

- [ ] **Step 2: Commit**

```bash
git add templates/integration/event-pipeline-flowchart.md
git commit -m "feat: add event pipeline flowchart template"
```

### Task 10: Create Request Lifecycle Sequence Diagram

**Files:**
- Create: `templates/integration/request-lifecycle-sequence.md`

- [ ] **Step 1: Create request-lifecycle-sequence.md**

Extract the "Sequence Diagram — Request Lifecycle" template from `CLAUDE.md:222-249`. Wrap in note wrapper with:
- tags: `[architecture, diagram, sequence, mermaid, api, request]`
- Context callout explaining this is a standard HTTP request flow through a layered API
- Notes section with link to the sequence snippet kit for adding conditionals, loops, etc.

- [ ] **Step 2: Commit**

```bash
git add templates/integration/request-lifecycle-sequence.md
git commit -m "feat: add request lifecycle sequence diagram template"
```

### Task 11: Create Webhook/Async Sequence Diagram

**Files:**
- Create: `templates/integration/webhook-async-sequence.md`

- [ ] **Step 1: Create webhook-async-sequence.md**

Extract the "Sequence Diagram — Webhook / Async Flow" template from `CLAUDE.md:283-308`. Wrap in note wrapper with:
- tags: `[architecture, diagram, sequence, mermaid, webhook, async]`
- Context callout explaining this is for outbound webhooks, event publishing, or async processing
- Notes section with hints on retry logic and error handling patterns

- [ ] **Step 2: Commit**

```bash
git add templates/integration/webhook-async-sequence.md
git commit -m "feat: add webhook async sequence diagram template"
```

### Task 12: Create State Diagram (NEW)

**Files:**
- Create: `templates/integration/state-diagram.md`

- [ ] **Step 1: Create state-diagram.md**

This is a NEW template (not in CLAUDE.md). Create a generic state machine diagram using Mermaid `stateDiagram-v2` with:
- Example: Order lifecycle (Draft → Submitted → Processing → Fulfilled / Cancelled)
- Fork/join for parallel states where appropriate
- Notes on states with entry/exit actions
- Uses project color conventions where Mermaid state diagrams support styling
- tags: `[architecture, diagram, state, mermaid, workflow]`
- Context callout explaining this is a generic state machine for modeling workflows, order lifecycles, CI/CD pipelines, etc.
- Notes section with hints on adding states, transitions, and guards

- [ ] **Step 2: Commit**

```bash
git add templates/integration/state-diagram.md
git commit -m "feat: add state diagram template"
```

---

## Chunk 5: Reference Files

### Task 13: Create Shape Reference

**Files:**
- Create: `templates/reference/shape-reference.md`

- [ ] **Step 1: Create directory and file**

```bash
mkdir -p templates/reference
```

Extract both shape reference tables from `CLAUDE.md:729-750` (Mermaid and D2). Wrap in note wrapper with:
- tags: `[architecture, diagram, reference]`
- Context callout explaining this is a quick-reference for node shapes in both Mermaid and D2
- Two sections: `## Mermaid Shapes` and `## D2 Shapes`

- [ ] **Step 2: Commit**

```bash
git add templates/reference/shape-reference.md
git commit -m "feat: add shape reference"
```

### Task 14: Create Color Palette Reference

**Files:**
- Create: `templates/reference/color-palette.md`

- [ ] **Step 1: Create color-palette.md**

Extract the color palette table from `CLAUDE.md:755-766`. Wrap in note wrapper with:
- tags: `[architecture, diagram, reference, color]`
- Context callout explaining this is the dark-mode color palette used across all templates
- Include all four columns: Layer, Fill, Stroke, Text

- [ ] **Step 2: Commit**

```bash
git add templates/reference/color-palette.md
git commit -m "feat: add color palette reference"
```

### Task 15: Create Sequence Snippet Kit

**Files:**
- Create: `templates/reference/sequence-snippet-kit.md`

- [ ] **Step 1: Create sequence-snippet-kit.md**

Extract the "Useful additions" code block from `CLAUDE.md:253-275`. Wrap in note wrapper with:
- tags: `[architecture, diagram, reference, sequence, mermaid]`
- Context callout explaining these are copy-paste snippets for enhancing sequence diagrams
- Separate each snippet (conditional, loop, annotation, highlight) with a brief label

- [ ] **Step 2: Commit**

```bash
git add templates/reference/sequence-snippet-kit.md
git commit -m "feat: add sequence diagram snippet kit"
```

---

## Chunk 6: Starters and Index

### Task 16: Create Blank Mermaid Starter

**Files:**
- Create: `templates/starters/blank-mermaid.md`

- [ ] **Step 1: Create directory and file**

```bash
mkdir -p templates/starters
```

Create a minimal Mermaid flowchart starter with:
- Empty `flowchart TD` with two placeholder subgraphs using the dark-mode palette
- A couple of placeholder nodes and one edge
- tags: `[architecture, diagram, mermaid, starter]`
- Context callout: "A minimal Mermaid flowchart with the project color palette applied. Replace the placeholder nodes and customize."

- [ ] **Step 2: Commit**

```bash
git add templates/starters/blank-mermaid.md
git commit -m "feat: add blank mermaid starter template"
```

### Task 17: Create Blank D2 Starter

**Files:**
- Create: `templates/starters/blank-d2.md`

- [ ] **Step 1: Create blank-d2.md**

Create a minimal D2 diagram starter with:
- `direction: down` and two placeholder containers using the dark-mode palette
- A couple of placeholder nodes and one connection
- tags: `[architecture, diagram, d2, starter]`
- Context callout: "A minimal D2 diagram with the project color palette applied. Replace the placeholder nodes and customize."

- [ ] **Step 2: Commit**

```bash
git add templates/starters/blank-d2.md
git commit -m "feat: add blank D2 starter template"
```

### Task 18: Create Index File

**Files:**
- Create: `templates/index.md`

- [ ] **Step 1: Create index.md**

Create the browsable index with:
- Frontmatter: `tags: [architecture, diagram, index]`
- Brief intro paragraph
- Sections: System Design, Data Modeling, Infrastructure, Integration, Reference, Starters
- Each entry as a wiki-link with one-line description, e.g.:
  - `[[system-design/system-overview-flowchart|System Overview Flowchart]]` — Layered architecture, Clean Architecture style (Mermaid)
- Tool info summary (Mermaid = built-in, D2 = plugin required)
- Color palette quick-reference table

- [ ] **Step 2: Verify all links match actual filenames**

Check that every wiki-link in index.md corresponds to an actual file in the templates directory.

- [ ] **Step 3: Commit**

```bash
git add templates/index.md
git commit -m "feat: add browsable index for template library"
```

---

## Summary

| Chunk | Tasks | Files Created |
|-------|-------|---------------|
| 1. System Design | 1-4 | 4 templates |
| 2. Data Modeling | 5-6 | 2 templates |
| 3. Infrastructure | 7-8 | 2 templates (1 new) |
| 4. Integration | 9-12 | 4 templates (1 new) |
| 5. Reference | 13-15 | 3 reference files |
| 6. Starters + Index | 16-18 | 2 starters (new) + 1 index |

**Total: 18 tasks, 18 files**
