---
tags: [architecture, diagram, mermaid, planning, git]
project: <ProjectName>
created: <date>
---

# Git Branching Strategy

> [!info] Context
> A Mermaid gitgraph showing branching patterns. Use for documenting your team's branching strategy, release process, or Git workflow conventions.

## Diagram

```mermaid
gitGraph
    commit id: "init"
    commit id: "base setup"

    branch feature/auth
    checkout feature/auth
    commit id: "add login"
    commit id: "add signup"
    checkout main
    merge feature/auth id: "merge auth" tag: "v0.1.0"

    branch feature/dashboard
    checkout feature/dashboard
    commit id: "dashboard layout"
    commit id: "add charts"

    checkout main
    commit id: "hotfix: security patch" type: HIGHLIGHT

    checkout feature/dashboard
    merge main id: "rebase main"
    commit id: "final polish"

    checkout main
    merge feature/dashboard id: "merge dashboard" tag: "v0.2.0"

    branch release/1.0
    checkout release/1.0
    commit id: "bump version"
    commit id: "release notes"
    checkout main
    merge release/1.0 id: "release 1.0" tag: "v1.0.0"
```

## Notes

- Use `branch`, `checkout`, `commit`, and `merge` to model your workflow
- Add `tag:` to mark releases
- Use `type: HIGHLIGHT` for important commits (hotfixes, breaking changes)
- Adapt to your strategy: trunk-based, gitflow, GitHub flow, etc.
- Mermaid gitgraph has limited styling — focus on illustrating the branching model
