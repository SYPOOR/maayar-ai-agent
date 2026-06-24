# Intelligence Orchestration Workflow

Capability execution, validation, and signal assembly workflow.

---

## Orchestration Workflow

```
  Enriched Context (from Data Acquisition)
       │
       ▼
  ┌─────────────────────────┐
  │ Intelligence Layer      │
  │ Dispatch Controller     │
  └────────────┬────────────┘
               │
    ┌──────────┼──────────┬──────────┐
    ▼          ▼          ▼          ▼
 ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐
 │ Geo  │  │ Crop │  │ Ops  │  │Disease│   ← Parallel Execution
 │Analysis│ │Analysis│ │Ready │  │Exposure│
 └──┬───┘  └──┬───┘  └──┬───┘  └──┬───┘
    │         │         │         │
    └─────────┴────┬────┴─────────┘
                   ▼
        ┌─────────────────────┐
        │ Signal Validation │
        └─────────┬─────────┘
                  ▼
        ┌─────────────────────┐
        │ Domain Signal       │
        │ Assembly            │
        └─────────┬─────────┘
                  ▼
        Classification Services
```

---

## Per-Capability Execution

| Step | Action |
|------|--------|
| 1 | Receive enriched assessment context |
| 2 | Acquire domain-specific data dependencies |
| 3 | Execute domain analysis |
| 4 | Generate domain signal per output contract |
| 5 | Return signal to Intelligence Layer |

---

## Execution Policies

| Capability | Timeout | Retry |
|------------|---------|-------|
| Geospatial Analysis | 30s | 2 retries |
| Crop Context Analysis | 15s | 1 retry |
| Operational Readiness | 10s | No retry |
| Disease Exposure Analysis | 20s | 1 retry |

---

## Signal Validation

```
  Domain Signal
       │
       ▼
  Schema Valid? ──No──▶ Retry Capability
       │ Yes
       ▼
  Confidence OK? ──No──▶ Flag Degraded
       │ Yes
       ▼
  Timestamp Fresh? ──No──▶ Flag Degraded
       │ Yes
       ▼
  Accept Signal
```

→ Architecture: [../architecture/intelligence-orchestration.md](../architecture/intelligence-orchestration.md)
