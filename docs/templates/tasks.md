# Feature: [Feature Name]

> Generated from: `docs/tasks/<slug>/techspec.md`

## Summary

| # | Task | Area | Type | Complexity | Blocked By | Parallelizable | Status |
|---|------|------|------|------------|------------|----------------|--------|
| 01 | [Task title] | `apps/...` | implementation | low | - | yes | pending |
| 02 | [Task title] | `packages/...` | integration | medium | 01 | no | pending |

## Execution Tracks

### Track A: [Domain/Area Name] (Sequential)

Tasks that must be executed in order due to dependencies.

1. `01_task.md` - [Brief description]
2. `02_task.md` - [Brief description] *(blocked by 01)*

### Track B: [Domain/Area Name] (Parallel)

Tasks that can be executed simultaneously after their dependencies are met.

- `03_task.md` - [Brief description]
- `04_task.md` - [Brief description]

## Dependency Graph

```
01 ─► 02 ─► 05
      │
03 ───┴───► 06
      │
04 ───┘
```

## Task Status Legend

| Status | Description |
|--------|-------------|
| `pending` | Not started |
| `in-progress` | Currently being worked on |
| `completed` | Done and verified |
| `cancelled` | No longer needed |

## Notes

- Each task file (`NN_task.md`) follows the template at `docs/templates/task.md`
- Update this summary when task status changes
- Refer to `techspec.md` for technical decisions and `prd.md` for product context
