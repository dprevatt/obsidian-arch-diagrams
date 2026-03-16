---
tags: [architecture, diagram, d2, infrastructure, network]
project: <ProjectName>
created: <date>
---

# Network Topology

> [!info] Context
> A general-purpose network topology diagram showing VLANs, routing, and device placement. Use for documenting office networks, homelab networking, or cloud VPC layouts.

## Diagram

```d2
direction: down

internet: Internet {shape: cloud}

firewall: Firewall / Router

core_switch: Core Switch

server_vlan: {
  label: "Server VLAN"
  style.fill: "#1a3a2a"
  style.stroke: "#4aff91"

  web: Web Server
  app: App Server
  db: DB Server {shape: cylinder}
}

client_vlan: {
  label: "Client VLAN"
  style.fill: "#1e3a5f"
  style.stroke: "#4a9eff"

  workstations: Workstations
  ap: Wireless AP
}

mgmt_vlan: {
  label: "Management VLAN"
  style.fill: "#2a1a3a"
  style.stroke: "#cc4aff"

  monitoring: Monitoring
  admin: Admin Console
}

internet -> firewall
firewall -> core_switch
core_switch -> server_vlan
core_switch -> client_vlan
core_switch -> mgmt_vlan
```

## Notes

- Requires the `d2-obsidian` plugin
- Add/remove VLANs and devices as needed
- Add port numbers or bandwidth labels to connections
- Customize IP ranges in VLAN labels
