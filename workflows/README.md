# Workflows

Process and pipeline documentation for the Maayar platform.

---

## Workflow Index

| Workflow | Description | Documentation |
|----------|-------------|---------------|
| **Risk Assessment Pipeline** | End-to-end assessment lifecycle | [risk-assessment-pipeline.md](./risk-assessment-pipeline.md) |
| **Data Acquisition Strategy** | Data ingestion and enrichment | [data-acquisition-strategy.md](./data-acquisition-strategy.md) |
| **Intelligence Orchestration** | Capability execution and assembly | [intelligence-orchestration.md](./intelligence-orchestration.md) |
| **Decision Support Workflow** | Classification to report delivery | [decision-support-workflow.md](./decision-support-workflow.md) |
| **Operational Workflows** | Error handling, monitoring, recovery | [operational-workflows.md](./operational-workflows.md) |

---

## Master Pipeline

```
  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
  │ 1. Intake &  │───▶│ 2. Data      │───▶│ 3. Intelligence│───▶│ 4. Decision  │───▶│ 5. Report    │
  │ Validation   │    │ Acquisition  │    │ Orchestration │    │ Support      │    │ Delivery     │
  └──────────────┘    └──────────────┘    └──────────────┘    └──────────────┘    └──────────────┘
```

---

## Workflow Principles

| Principle | Description |
|-----------|-------------|
| Deterministic stages | Defined inputs, outputs, and success criteria per stage |
| Idempotent operations | Consistent results for identical inputs |
| Graceful degradation | Pipeline continues with partial capability data |
| Full auditability | Every stage transition logged with metadata |

---

## Related Documentation

- [Architecture](../architecture/README.md)
- [Capabilities](../capabilities/README.md)
