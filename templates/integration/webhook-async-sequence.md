---
tags: [architecture, diagram, sequence, mermaid, webhook, async]
project: <ProjectName>
created: <date>
---

# Webhook / Async Flow — Sequence Diagram

> [!info] Context
> An asynchronous processing pattern showing event publishing, message consumption, webhook delivery, and retry logic. Use for outbound webhooks, event-driven architectures, or background job flows.

## Diagram

```mermaid
sequenceDiagram
    autonumber
    participant SVC as Service
    participant QUEUE as Message Queue
    participant WORKER as Background Worker
    participant EXT as External System
    participant NOTIFY as Notification

    SVC->>QUEUE: Publish event
    Note right of QUEUE: Async boundary

    QUEUE->>WORKER: Consume message
    activate WORKER

    WORKER->>EXT: Deliver payload (webhook)
    EXT-->>WORKER: 200 Acknowledged

    alt Delivery success
        WORKER->>NOTIFY: Send confirmation
    else Delivery failure
        WORKER->>QUEUE: Re-queue (retry)
    end

    deactivate WORKER
```

## Notes

- Add retry count limits with `loop Retry (max N)` blocks
- Add dead-letter queue handling for permanent failures
- Customize participant names to match your infrastructure
