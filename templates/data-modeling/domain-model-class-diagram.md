---
tags: [architecture, diagram, class-diagram, mermaid, domain-model]
project: <ProjectName>
created: <date>
---

# Domain Model — Class Diagram

> [!info] Context
> A Clean Architecture domain model showing entities, aggregate roots, value objects, and enums. Use for EF Core models, DDD aggregates, or any OOP structure.

## Diagram

```mermaid
classDiagram
    class Entity {
        <<abstract>>
        +Guid Id
        +DateTime CreatedAt
        +DateTime UpdatedAt
    }

    class AggregateRoot {
        <<abstract>>
        +List~DomainEvent~ DomainEvents
        +AddDomainEvent(event)
        +ClearDomainEvents()
    }

    class User {
        +string Email
        +string Name
        +OrganizationId OrgId
        +IsActive bool
        +Deactivate()
    }

    class Organization {
        +string Name
        +string Slug
        +List~Project~ Projects
        +AddProject(project) Project
    }

    class Project {
        +string Name
        +ProjectStatus Status
        +Guid OrgId
        +List~Mapping~ Mappings
        +Publish()
        +Archive()
    }

    class Mapping {
        +string SourceField
        +string TargetField
        +TransformType Transform
        +Validate() bool
    }

    class ProjectStatus {
        <<enumeration>>
        Draft
        Active
        Archived
    }

    Entity <|-- AggregateRoot
    AggregateRoot <|-- User
    AggregateRoot <|-- Organization
    AggregateRoot <|-- Project
    Entity <|-- Mapping

    Organization "1" --> "0..*" Project : owns
    Project "1" --> "0..*" Mapping : contains
    User "*" --> "1" Organization : belongs to
    Project --> ProjectStatus : status
```

## Notes

- Rename entities to match your domain
- Add/remove properties and methods as needed
- Use `<<abstract>>` for base classes and `<<enumeration>>` for enums
- Relationship syntax: `"1" --> "0..*"` for cardinality
