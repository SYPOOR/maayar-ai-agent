# Capabilities

Domain capability specifications for the Maayar Intelligence Layer.

---

## Capability Model

Maayar's Intelligence Layer comprises **four domain capability modules**, each analyzing a distinct dimension of agricultural risk and producing standardized domain signals for Classification Services.

```
                    ┌─────────────────────────┐
                    │  Intelligence Layer     │
                    │  (Orchestration)        │
                    └────────────┬────────────┘
                                 │
         ┌───────────┬───────────┼───────────┬───────────┐
         ▼           ▼           ▼           ▼           │
  ┌────────────┐┌────────────┐┌────────────┐┌────────────┐│
  │Geospatial  ││Crop Context││Operational ││Disease     ││
  │Analysis    ││Analysis    ││Readiness   ││Exposure    ││
  └─────┬──────┘└─────┬──────┘└─────┬──────┘└─────┬──────┘│
        │             │             │             │       │
        └─────────────┴─────────────┴─────────────┘       │
                                 │                         │
                                 ▼                         │
                    ┌─────────────────────────┐            │
                    │  Domain Signal Assembly │◀───────────┘
                    └─────────────────────────┘
```

---

## Capability Catalog

| Capability Domain | Risk Dimension | Documentation |
|-------------------|----------------|---------------|
| **Geospatial Analysis** | Environmental and climate exposure | [geospatial-intelligence.md](./geospatial-intelligence.md) |
| **Crop Context Analysis** | Crop-specific phenological risk | [crop-context-analysis.md](./crop-context-analysis.md) |
| **Operational Readiness** | Farm preparedness and infrastructure | [operational-readiness.md](./operational-readiness.md) |
| **Disease Exposure Analysis** | Pathogen and pest pressure | [disease-exposure-analysis.md](./disease-exposure-analysis.md) |

---

## Capability Contract

All capability modules adhere to a shared contract:

| Aspect | Specification |
|--------|---------------|
| **Invocation** | Intelligence Layer dispatches with assessment context |
| **Input** | Enriched farm context from Data Acquisition Layer |
| **Output** | Standardized domain signal object |
| **Independence** | No inter-capability communication |
| **Timeout** | Domain-specific execution limits |

→ Output contract: [output-contract.md](./output-contract.md)  
→ Domain model: [domain-model.md](./domain-model.md)

---

## Design Principles

| Principle | Description |
|-----------|-------------|
| Single responsibility | One risk dimension per capability |
| Structured output | Machine-readable domain signals |
| Provenance tracking | Data source attribution in every signal |
| Confidence reporting | Self-reported confidence per capability |
| Independent deployment | Capabilities evolve without pipeline changes |

---

## Related Documentation

- [Intelligence Orchestration](../architecture/intelligence-orchestration.md)
- [Classification Services](../architecture/classification-services.md)
