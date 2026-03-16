---
tags: [architecture, diagram, d2, starter]
project: <ProjectName>
created: <date>
---

# Blank D2 Starter

> [!info] Context
> A minimal D2 diagram with the project color palette applied. Replace the placeholder nodes and customize.

## Diagram

```d2
direction: down

layer1: {
  label: "Layer 1"
  style.fill: "#1e3a5f"
  style.stroke: "#4a9eff"

  a: Node A
  b: Node B
}

layer2: {
  label: "Layer 2"
  style.fill: "#1a3a2a"
  style.stroke: "#4aff91"

  c: Node C
  d: Node D
}

layer1.a -> layer2.c
layer1.b -> layer2.d
```

## Notes

- Requires the `d2-obsidian` plugin
- Rename containers and nodes to match your system
- See [[reference/color-palette|Color Palette]] for all available colors
- See [[reference/shape-reference|Shape Reference]] for D2 shape syntax
