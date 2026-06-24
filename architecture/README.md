# Architecture

Enterprise architecture documentation for the Maayar Agricultural Risk Intelligence Platform.

---

## Documentation Map

| Document | Description |
|----------|-------------|
| [system-overview.md](./system-overview.md) | Platform context and high-level design |
| [platform-architecture.md](./platform-architecture.md) | Layered architecture specification |
| [intelligence-orchestration.md](./intelligence-orchestration.md) | Intelligence Layer design |
| [assessment-core.md](./assessment-core.md) | Assessment Core lifecycle |
| [classification-services.md](./classification-services.md) | Risk classification and synthesis |
| [decision-support-layer.md](./decision-support-layer.md) | Decision support output model |
| [data-acquisition-layer.md](./data-acquisition-layer.md) | Data ingestion and enrichment |
| [deployment-topology.md](./deployment-topology.md) | Cloud deployment architecture |
| [operational-considerations.md](./operational-considerations.md) | NFRs, resilience, observability |
| [future-evolution.md](./future-evolution.md) | Platform evolution roadmap |

### Supporting Documentation

| Section | Description |
|---------|-------------|
| [components/](./components/README.md) | Component-level specifications |
| [data-flows/](./data-flows/README.md) | Information flow documentation |
| [diagrams/](./diagrams/README.md) | Architecture diagram index |
| [decisions/](./decisions/README.md) | Architecture Decision Records |

---

## Layered Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    PRESENTATION LAYER                        │
└────────────────────────────┬────────────────────────────────┘
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                      API GATEWAY LAYER                       │
└────────────────────────────┬────────────────────────────────┘
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                  RISK INTELLIGENCE PIPELINE                   │
│                                                              │
│  Data Acquisition ──▶ Intelligence ──▶ Assessment Core     │
│                            │                    │            │
│                            ▼                    ▼            │
│                     Capability Domains   Classification      │
│                                               Services       │
│                                                    │         │
│                                                    ▼         │
│                                          Decision Support    │
└────────────────────────────┬────────────────────────────────┘
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                     DATA PLATFORM LAYER                      │
└─────────────────────────────────────────────────────────────┘
```

---

## Design Principles

| Principle | Description |
|-----------|-------------|
| **Layered separation** | Each layer has defined responsibilities and interfaces |
| **Capability modularity** | Domain capabilities evolve independently within contracts |
| **Auditable outputs** | Every assessment output traces to source capabilities and data |
| **Graceful degradation** | Partial capability results produce flagged, reduced-confidence output |
| **Cloud-native resilience** | Containerized, horizontally scalable, stateless where possible |

---

## Related Documentation

- [Capabilities](../capabilities/README.md)
- [Workflows](../workflows/README.md)
- [Technology](../technology/README.md)
