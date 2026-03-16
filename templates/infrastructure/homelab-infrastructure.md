---
tags: [architecture, diagram, d2, infrastructure, homelab, proxmox]
project: <ProjectName>
created: <date>
---

# Homelab Infrastructure

> [!info] Context
> A homelab infrastructure diagram showing Proxmox host with VMs, LXC containers, storage targets, and edge/proxy layer. Use for documenting self-hosted setups.

## Diagram

```d2
direction: down

internet: {
  label: "Internet"
  style.fill: "#1a1a2e"
  style.stroke: "#4a9eff"

  user: End User {shape: person}
  cf: Cloudflare {shape: cloud}
}

edge: {
  label: "Edge / Proxy"
  style.fill: "#1e2a1a"
  style.stroke: "#4aff70"

  proxy: Nginx Proxy Manager
  ssl: SSL Termination
}

proxmox: {
  label: "Proxmox Host"
  style.fill: "#1e1a2e"
  style.stroke: "#9966ff"

  apps: {
    label: "VM: App Server"
    app: Application
    api: API Layer
  }

  data: {
    label: "VM: Data"
    pg: PostgreSQL {shape: cylinder}
    redis: Redis {shape: cylinder}
  }

  automation: {
    label: "VM: Automation"
    n8n: n8n
    ha: Home Assistant
  }

  containers: {
    label: "LXC Containers"
    dns: AdGuard DNS
    mon: Monitoring
  }
}

storage: {
  label: "Storage"
  nas: NAS / NFS {shape: cylinder}
  backup: Backup Target {shape: cylinder}
}

internet.user -> internet.cf
internet.cf -> edge.proxy
edge.proxy -> edge.ssl
edge.ssl -> proxmox.apps.app
edge.ssl -> proxmox.automation.n8n
edge.ssl -> proxmox.automation.ha
proxmox.apps.app -> proxmox.data.pg
proxmox.apps.app -> proxmox.data.redis
proxmox.automation.n8n -> proxmox.automation.ha
proxmox.apps -> storage.nas
proxmox.data -> storage.nas
proxmox -> storage.backup
```

## Notes

- Requires the `d2-obsidian` plugin
- Add/remove VMs and LXC containers as needed
- D2's auto-layout keeps nested groups readable as they grow
- Customize service names, add port labels to connections
