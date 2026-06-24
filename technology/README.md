# Technology

Technology landscape and engineering decisions for the Maayar platform.

---

## Documentation

| Document | Description |
|----------|-------------|
| [stack-overview.md](./stack-overview.md) | Technology stack by layer |
| [technology-decisions.md](./technology-decisions.md) | Key technology choices |
| [data-platform.md](./data-platform.md) | Data storage and caching |
| [infrastructure.md](./infrastructure.md) | Cloud infrastructure and deployment |
| [integrations.md](./integrations.md) | External data integrations |
| [observability.md](./observability.md) | Monitoring and operational telemetry |

---

## Technology Landscape

```
  ┌─────────────────────────────────────────────────────────┐
  │  PRESENTATION          Web Application (SPA)            │
  ├─────────────────────────────────────────────────────────┤
  │  API                   API Gateway (REST)               │
  ├─────────────────────────────────────────────────────────┤
  │  INTELLIGENCE          Orchestration + Capability Svc   │
  ├─────────────────────────────────────────────────────────┤
  │  DATA                  PostgreSQL  ·  Redis               │
  ├─────────────────────────────────────────────────────────┤
  │  INFRASTRUCTURE        Docker  ·  Microsoft Azure       │
  ├─────────────────────────────────────────────────────────┤
  │  INTEGRATIONS          NASA POWER  ·  CHIRPS            │
  └─────────────────────────────────────────────────────────┘
```

---

## Decision Governance

Technology choices are documented as Architecture Decision Records:

→ [Architecture Decisions](../architecture/decisions/README.md)

---

## Scope Note

This documentation describes technology **roles and integration patterns**. Version pinning, implementation configurations, and internal processing details are maintained in the private production repository.
