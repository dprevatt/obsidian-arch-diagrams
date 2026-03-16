---
tags: [architecture, diagram, d2, microservices, system-design]
project: <ProjectName>
created: 2026-03-16
---

# Microservices Communication

> [!info] Context
> A microservices architecture showing sync (REST/gRPC) and async (event bus) communication patterns between services. Use for documenting service-to-service interactions in distributed systems.

## Diagram

```d2
direction: down

# API Gateway
api_gateway: API Gateway {
  shape: rectangle
  style: {
    fill: "#1a3a2a"
    stroke: "#4aff91"
    font-color: "#4aff91"
    bold: true
  }
}

# Services
user_service: User Service {
  shape: rectangle
  style: {
    fill: "#1e3a5f"
    stroke: "#4a9eff"
    font-color: "#4a9eff"
  }
}

order_service: Order Service {
  shape: rectangle
  style: {
    fill: "#1e3a5f"
    stroke: "#4a9eff"
    font-color: "#4a9eff"
  }
}

payment_service: Payment Service {
  shape: rectangle
  style: {
    fill: "#1e3a5f"
    stroke: "#4a9eff"
    font-color: "#4a9eff"
  }
}

notification_service: Notification Service {
  shape: rectangle
  style: {
    fill: "#1e3a5f"
    stroke: "#4a9eff"
    font-color: "#4a9eff"
  }
}

inventory_service: Inventory Service {
  shape: rectangle
  style: {
    fill: "#1e3a5f"
    stroke: "#4a9eff"
    font-color: "#4a9eff"
  }
}

# Event Bus
event_bus: Event Bus {
  shape: queue
  style: {
    fill: "#1a1e2e"
    stroke: "#66aaff"
    font-color: "#66aaff"
    bold: true
  }
}

# External Systems
stripe: Stripe API {
  shape: cloud
  style: {
    fill: "#2e1a1a"
    stroke: "#ff4a4a"
    font-color: "#ff4a4a"
  }
}

# Sync connections: Gateway -> Services (REST)
api_gateway -> user_service: REST
api_gateway -> order_service: REST
api_gateway -> payment_service: REST
api_gateway -> inventory_service: REST

# Sync connections: Service-to-Service (gRPC)
order_service -> inventory_service: gRPC
order_service -> payment_service: gRPC
payment_service -> stripe: REST

# Async connections: Services -> Event Bus (publishes)
order_service -> event_bus: publishes\nOrderPlaced
payment_service -> event_bus: publishes\nPaymentProcessed
inventory_service -> event_bus: publishes\nStockUpdated

# Async connections: Event Bus -> Services (subscribes)
event_bus -> notification_service: subscribes\nOrderPlaced,\nPaymentProcessed
event_bus -> inventory_service: subscribes\nOrderPlaced
event_bus -> order_service: subscribes\nPaymentProcessed
```

## Notes

- Requires the `d2-obsidian` plugin
- Add/remove services as needed for your domain
- Label connections with protocols (REST, gRPC, WebSocket)
- Use solid arrows for sync; async flows route through the event bus
- The event bus shape (`queue`) visually distinguishes async from sync paths
- Consider grouping tightly coupled services inside a D2 container block
- Replace `Stripe API` with whichever third-party payment or external service applies
- Add retry/circuit-breaker annotations on sync connections where resilience matters
