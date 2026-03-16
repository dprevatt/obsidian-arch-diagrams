---
tags: [architecture, diagram, erd, mermaid, database]
project: <ProjectName>
created: <date>
---

# Database ERD

> [!info] Context
> A database schema diagram showing tables, columns, types, and relationships. Use for database design, EF Core schema review, or data modeling.

## Diagram

```mermaid
erDiagram
    users {
        uuid id PK
        string email
        string name
        uuid org_id FK
        bool is_active
        timestamp created_at
        timestamp updated_at
    }

    organizations {
        uuid id PK
        string name
        string slug
        timestamp created_at
    }

    projects {
        uuid id PK
        uuid org_id FK
        string name
        string status
        timestamp created_at
        timestamp updated_at
    }

    mappings {
        uuid id PK
        uuid project_id FK
        string source_field
        string target_field
        string transform_type
        jsonb config
    }

    audit_logs {
        uuid id PK
        uuid user_id FK
        string entity_type
        uuid entity_id
        string action
        jsonb before_state
        jsonb after_state
        timestamp occurred_at
    }

    users ||--o{ audit_logs : "generates"
    organizations ||--o{ users : "has"
    organizations ||--o{ projects : "owns"
    projects ||--o{ mappings : "contains"
```

## Notes

- Rename tables and columns to match your schema
- Use PK/FK markers for primary and foreign keys
- Relationship syntax: `||--o{` (one-to-many), `||--||` (one-to-one), `}o--o{` (many-to-many)
- Add/remove tables as needed
