# obsidian-arch-diagrams

A library of architecture diagram starter templates for [Obsidian](https://obsidian.md), using **Mermaid** (built-in) and **D2** (plugin). Copy a template, drop it in a note, and customize from there.

Designed for software and infrastructure diagrams — system architecture, sequences, ERDs, homelab layouts, and C4 context/container diagrams.

-----

## What’s Inside

|File                      |Description                                                                         |
|--------------------------|------------------------------------------------------------------------------------|
|[`CLAUDE.md`](./CLAUDE.md)|Full template library with index, all templates, shape references, and color palette|

### Templates at a glance

**🟦 Flowcharts (Mermaid)**

- Layered system architecture (Clean Architecture style)
- Event / integration pipeline (n8n, webhooks, automation)

**🟩 Sequence Diagrams (Mermaid)**

- HTTP request lifecycle through a layered API
- Async webhook / background worker flow
- Snippet kit — conditionals, loops, annotations, highlights

**🟨 Class & Data Diagrams (Mermaid)**

- Domain model with abstract base classes, aggregates, enums
- Database ERD with PKs, FKs, and column types

**🟥 Architecture & Infrastructure (D2)**

- Clean Architecture system diagram with auto-layout
- Homelab / Proxmox infrastructure (VMs, LXC containers, storage)
- C4 Context — system boundary, actors, external systems
- C4 Container — internal containers, drill-down from context

-----

## Setup

### Mermaid

Nothing to install. Obsidian renders ````mermaid` fenced blocks natively.

### D2

D2 requires a local binary and the community plugin.

**1. Install D2**

|Platform              |Command                                                                    |
|----------------------|---------------------------------------------------------------------------|
|Arch Linux            |`yay -S d2`                                                                |
|macOS (Homebrew)      |`brew install d2`                                                          |
|macOS / Linux (script)|`curl -fsSL https://d2lang.com/install.sh | sh`                            |
|Windows (Scoop)       |`scoop install d2`                                                         |
|Windows (Winget)      |`winget install terrastruct.d2`                                            |
|Any platform          |[Download binary from releases](https://github.com/terrastruct/d2/releases)|

Verify: `d2 --version`

**2. Install the Obsidian plugin**

1. Obsidian → Settings → Community Plugins → Browse
1. Search **D2** → Install → Enable
1. In plugin settings, confirm the D2 binary path (e.g. `/usr/bin/d2` or `/usr/local/bin/d2`)

**3. Use it**
Use ````d2` fenced blocks in any note — diagrams render inline.

-----

## Usage

1. Open [`CLAUDE.md`](./CLAUDE.md) and find the template you want
1. Copy the fenced code block into your Obsidian note
1. Wrap it in the [note wrapper template](./CLAUDE.md#obsidian-note-wrapper) for consistent frontmatter
1. Customize node names, subgraph labels, and edges for your context

### Color conventions

All templates share a consistent dark-mode color palette:

|Layer            |Color             |
|-----------------|------------------|
|Client / UI      |🔵 Blue `#4a9eff`  |
|API / Gateway    |🟢 Green `#4aff91` |
|Domain / Core    |🟡 Amber `#ffaa4a` |
|Infrastructure   |🟣 Purple `#cc4aff`|
|External Systems |🔴 Red `#ff4a4a`   |
|Storage / Data   |🟠 Orange `#ff7044`|
|Automation / Jobs|💙 Slate `#66aaff` |

-----

## Why Mermaid + D2?

Both tools are diagram-as-code, meaning diagrams live in plain text files alongside your notes and can be version controlled.

**Mermaid** is built into Obsidian with no setup. It’s the best choice for sequence diagrams, ERDs, and class diagrams where it has first-class syntax support.

**D2** produces cleaner auto-layout for complex architecture and infrastructure diagrams. Its ELK layout engine keeps nested subgraphs (like Proxmox hosts with multiple VMs) readable as they grow — something Mermaid’s layout engine struggles with.

-----

## Contributing

PRs welcome — new templates, additional diagram types, or light-mode palette variants.