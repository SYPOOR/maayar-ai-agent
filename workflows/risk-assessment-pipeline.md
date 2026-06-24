# Risk Assessment Pipeline

End-to-end farm risk assessment lifecycle.

---

## Assessment Workflow Diagram

```
  ┌──────────┐
  │  User    │
  │  Request │
  └────┬─────┘
       │
       ▼
  ┌──────────────────────────────────────────────────────────┐
  │ PHASE 1: INTAKE & VALIDATION                             │
  │  · Receive farm context (boundary, crop, indicators)   │
  │  · Validate input schema and authorization               │
  │  · Initialize assessment session in Assessment Core      │
  └──────────────────────────┬───────────────────────────────┘
                             │
                             ▼
  ┌──────────────────────────────────────────────────────────┐
  │ PHASE 2: DATA ACQUISITION & ENRICHMENT                   │
  │  · Load farm profile from Data Platform                  │
  │  · Fetch external data (climate, precipitation)          │
  │  · Cache enrichment results                              │
  └──────────────────────────┬───────────────────────────────┘
                             │
                             ▼
  ┌──────────────────────────────────────────────────────────┐
  │ PHASE 3: INTELLIGENCE ORCHESTRATION                      │
  │  · Dispatch capability modules in parallel               │
  │  · Collect and validate domain signals                   │
  │  · Assemble signal package for classification            │
  └──────────────────────────┬───────────────────────────────┘
                             │
                             ▼
  ┌──────────────────────────────────────────────────────────┐
  │ PHASE 4: CLASSIFICATION & DECISION SUPPORT               │
  │  · Normalize and weight domain signals                   │
  │  · Assign risk tier and generate decomposition           │
  │  · Produce composite risk output                         │
  └──────────────────────────┬───────────────────────────────┘
                             │
                             ▼
  ┌──────────────────────────────────────────────────────────┐
  │ PHASE 5: DELIVERY                                        │
  │  · Persist assessment to Data Platform                   │
  │  · Return result to Presentation Layer                   │
  │  · Render assessment report                              │
  └──────────────────────────┬───────────────────────────────┘
                             │
                             ▼
                      Assessment Complete
```

---

## Phase Specifications

| Phase | Actor | Duration | Success Criteria |
|-------|-------|----------|------------------|
| Intake | API Gateway + Assessment Core | < 1s | Valid session created |
| Acquisition | Data Acquisition Layer | 2–15s | Enriched context available |
| Intelligence | Intelligence Layer | 5–30s | ≥ 1 valid domain signal |
| Classification | Classification Services | 1–3s | Composite output generated |
| Delivery | Decision Support + Presentation | < 1s | Report rendered |

---

## Related Documentation

- [Assessment Core](../architecture/assessment-core.md)
- [Data Acquisition Strategy](./data-acquisition-strategy.md)
- [Intelligence Orchestration](./intelligence-orchestration.md)
