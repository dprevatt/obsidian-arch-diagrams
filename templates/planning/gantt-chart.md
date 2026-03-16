---
tags: [architecture, diagram, mermaid, planning, gantt]
project: <ProjectName>
created: <date>
---

# Gantt Chart

> [!info] Context
> A Mermaid Gantt chart for project planning, sprint scheduling, or release timelines. Customize tasks, dates, and dependencies to match your project.

## Diagram

```mermaid
gantt
    title Project Timeline
    dateFormat YYYY-MM-DD
    excludes weekends

    section Planning
        Requirements gathering    :done, req, 2025-01-06, 5d
        Architecture design       :done, arch, after req, 5d
        Tech spike               :active, spike, after arch, 3d

    section Development
        Core API                 :api, after spike, 10d
        Frontend scaffold        :fe, after spike, 5d
        Auth integration         :auth, after api, 5d
        Feature A                :feat-a, after fe, 8d
        Feature B                :feat-b, after auth, 8d

    section Testing
        Integration tests        :test, after feat-a, 5d
        UAT                      :uat, after test, 5d
        Performance testing      :perf, after test, 3d

    section Release
        Staging deploy           :stage, after uat, 2d
        Production deploy        :milestone, prod, after stage, 0d
```

## Notes

- Use `done`, `active`, or `crit` to mark task status
- Use `after taskId` for dependencies
- Use `milestone` for zero-duration milestone markers
- `excludes weekends` skips Saturdays and Sundays
- Customize `dateFormat` as needed (YYYY-MM-DD is default)
