# Pipeline Runtime

Assessment Core and Intelligence Layer runtime component.

---

## Responsibilities

- Assessment session lifecycle management
- Pipeline stage sequencing and state persistence
- Capability dispatch and signal assembly
- Error routing and degradation handling

---

## Position in Architecture

```
  API Gateway ──▶ Pipeline Runtime ──▶ Classification Engine
                       │
                       ├── Capability Modules
                       ├── Data Acquisition
                       └── Data Platform
```

→ [Assessment Core](../assessment-core.md)  
→ [Intelligence Orchestration](../intelligence-orchestration.md)
