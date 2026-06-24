# Intelligence Orchestration

Architecture of the Intelligence Layer and capability orchestration patterns.

---

## Purpose

The Intelligence Layer coordinates **parallel execution** of domain capability modules, manages capability lifecycle within an assessment session, and assembles standardized domain signals for downstream Classification Services.

---

## Orchestration Model

```
                    ┌─────────────────────────┐
                    │   Assessment Core       │
                    │   (Session Context)     │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │   Intelligence Layer    │
                    │   Orchestration Engine  │
                    └────────────┬────────────┘
                                 │
              ┌──────────────────┼──────────────────┐
              │                  │                  │
              ▼                  ▼                  ▼
     ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
     │ Geospatial  │    │ Crop Context│    │ Operational │
     │ Analysis    │    │ Analysis    │    │ Readiness   │
     └──────┬──────┘    └──────┬──────┘    └──────┬──────┘
            │                  │                  │
            └──────────────────┼──────────────────┘
                               │
                               ▼
                    ┌─────────────┐
                    │  Disease    │
                    │  Exposure   │
                    │  Analysis   │
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────────────────┐
                    │  Domain Signal Assembly │
                    └─────────────────────────┘
```

---

## Orchestration Responsibilities

| Responsibility | Description |
|----------------|-------------|
| **Dispatch** | Invoke capability modules with assessment context |
| **Parallelism** | Execute independent capabilities concurrently |
| **Timeout management** | Enforce per-capability execution limits |
| **Signal validation** | Verify capability outputs against output contract |
| **Degradation handling** | Continue with partial results when capabilities fail |
| **Assembly** | Collect validated signals for Classification Services |

---

## Execution Strategy

| Aspect | Policy |
|--------|--------|
| **Default mode** | Parallel execution across all capability domains |
| **Blocking behavior** | Wait for all capabilities to complete or timeout |
| **Failure handling** | Retry transient failures; degrade on persistent failure |
| **Minimum threshold** | At least one valid capability signal required |
| **Partial flagging** | Assessments with missing domains flagged in output |

---

## State Management

Assessment session state is managed by the Assessment Core and persisted to the Data Platform, enabling:

- Session recovery after infrastructure interruption
- Assessment replay for audit and review
- Long-running assessment support

→ Assessment Core: [assessment-core.md](./assessment-core.md)  
→ Workflow: [../workflows/intelligence-orchestration.md](../workflows/intelligence-orchestration.md)

---

## Capability Independence

Capability modules operate under strict independence constraints:

| Constraint | Rationale |
|------------|-----------|
| No inter-capability communication | Isolation, testability, independent deployment |
| Standardized output contract | Uniform downstream processing |
| Independent data access | Each capability owns its data dependencies |
| Isolated failure domains | One capability failure does not cascade |

→ Capability catalog: [../capabilities/README.md](../capabilities/README.md)
