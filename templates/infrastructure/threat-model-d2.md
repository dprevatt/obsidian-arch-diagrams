---
tags: [architecture, diagram, d2, infrastructure, security, threat-model]
project: <ProjectName>
created: 2026-03-16
---

# Threat Model

> [!info] Context
> A threat modeling diagram showing trust boundaries, data flows, and threat zones. Use for security reviews, compliance documentation, or architecture risk analysis.

## Diagram

```d2
direction: right

# External / Untrusted Zone
external_zone: External / Untrusted {
  style: {
    fill: "#2e1a1a"
    stroke: "#ff4a4a"
    font-color: "#ff4a4a"
    stroke-dash: 5
    bold: true
  }

  end_user: End User {
    shape: person
    style: {
      fill: "#2e1a1a"
      stroke: "#ff4a4a"
      font-color: "#ff4a4a"
    }
  }

  third_party_api: Third-party API {
    shape: cloud
    style: {
      fill: "#2e1a1a"
      stroke: "#ff4a4a"
      font-color: "#ff4a4a"
    }
  }
}

# DMZ / Edge Zone
dmz_zone: DMZ / Edge {
  style: {
    fill: "#3a2a1a"
    stroke: "#ffaa4a"
    font-color: "#ffaa4a"
    stroke-dash: 5
    bold: true
  }

  load_balancer: Load Balancer {
    shape: rectangle
    style: {
      fill: "#3a2a1a"
      stroke: "#ffaa4a"
      font-color: "#ffaa4a"
    }
  }

  waf: WAF {
    shape: rectangle
    style: {
      fill: "#3a2a1a"
      stroke: "#ffaa4a"
      font-color: "#ffaa4a"
    }
  }

  api_gateway: API Gateway {
    shape: rectangle
    style: {
      fill: "#3a2a1a"
      stroke: "#ffaa4a"
      font-color: "#ffaa4a"
    }
  }
}

# Internal / Trusted Zone
internal_zone: Internal / Trusted {
  style: {
    fill: "#1a3a2a"
    stroke: "#4aff91"
    font-color: "#4aff91"
    stroke-dash: 5
    bold: true
  }

  app_server: App Server {
    shape: rectangle
    style: {
      fill: "#1a3a2a"
      stroke: "#4aff91"
      font-color: "#4aff91"
    }
  }

  auth_service: Auth Service {
    shape: rectangle
    style: {
      fill: "#1a3a2a"
      stroke: "#4aff91"
      font-color: "#4aff91"
    }
  }

  database: Database {
    shape: cylinder
    style: {
      fill: "#2e1e1a"
      stroke: "#ff7044"
      font-color: "#ff7044"
    }
  }
}

# Threat Zone Annotations
threat_zones: Threat Zones {
  style: {
    fill: "#1a1e2e"
    stroke: "#66aaff"
    font-color: "#66aaff"
    stroke-dash: 3
    bold: true
  }

  t1: T1: Public Attack Surface {
    style: {
      fill: "#1a1e2e"
      stroke: "#66aaff"
      font-color: "#66aaff"
    }
  }

  t2: T2: Edge Bypass Risk {
    style: {
      fill: "#1a1e2e"
      stroke: "#66aaff"
      font-color: "#66aaff"
    }
  }

  t3: T3: Internal Lateral Movement {
    style: {
      fill: "#1a1e2e"
      stroke: "#66aaff"
      font-color: "#66aaff"
    }
  }
}

# Data Flows
external_zone.end_user -> dmz_zone.load_balancer: HTTPS request\n[T1: MITM risk, DDoS]
external_zone.third_party_api -> dmz_zone.api_gateway: Webhook / callback\n[T1: spoofing risk]
dmz_zone.load_balancer -> dmz_zone.waf: forward\n[T2: rule bypass]
dmz_zone.waf -> dmz_zone.api_gateway: filtered request\n[T2: injection risk]
dmz_zone.api_gateway -> internal_zone.app_server: authenticated request\n[T2: token forgery]
dmz_zone.api_gateway -> internal_zone.auth_service: token validation\n[T2: replay attack]
internal_zone.app_server -> internal_zone.auth_service: authorize\n[T3: privilege escalation]
internal_zone.app_server -> internal_zone.database: query\n[T3: SQL injection]
internal_zone.auth_service -> internal_zone.database: read credentials\n[T3: data exfiltration]
```

## Notes

- Requires the `d2-obsidian` plugin
- Dashed borders (`style.stroke-dash: 5`) represent trust boundaries
- Add threat annotations to connections (e.g., "MITM risk", "injection risk")
- Customize zones and components to match your system's architecture
- Consider STRIDE categories when annotating threats:
  - **S**poofing, **T**ampering, **R**epudiation, **I**nformation Disclosure, **D**enial of Service, **E**levation of Privilege
- The `Threat Zones` annotation block maps numbered threats (T1, T2, T3) to boundary regions
- For compliance use cases (SOC 2, ISO 27001), export this diagram and attach to the relevant control evidence
- Expand the `Internal / Trusted` zone with additional microservices as your architecture grows
