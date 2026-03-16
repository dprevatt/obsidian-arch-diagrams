---
tags: [architecture, diagram, state, mermaid, workflow]
project: <ProjectName>
created: <date>
---

# State Diagram

> [!info] Context
> A generic state machine for modeling workflows, order lifecycles, CI/CD pipelines, or any process with defined states and transitions. Customize states and transitions to match your domain.

## Diagram

```mermaid
stateDiagram-v2
    [*] --> Draft

    Draft --> Submitted : Submit
    Submitted --> Processing : Approve
    Submitted --> Cancelled : Reject

    Processing --> fork_state
    state fork_state <<fork>>

    fork_state --> Fulfillment
    fork_state --> Billing

    state Fulfillment {
        Picking --> Shipping
        Shipping --> Delivered
    }

    state Billing {
        Invoicing --> Paid
    }

    Fulfillment --> join_state
    Billing --> join_state
    state join_state <<join>>

    join_state --> Completed

    Completed --> [*]
    Cancelled --> [*]
```

## Notes

- Replace states and transitions to match your domain
- Use `<<fork>>` and `<<join>>` for parallel processing
- Use `<<choice>>` for conditional transitions
- Add notes with `note right of StateName: description`
- Mermaid state diagrams have limited styling support compared to flowcharts
