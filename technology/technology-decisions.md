# Technology Decisions

Summary of key technology decisions for the Maayar platform.

---

## Decision Summary

| Decision | Choice | ADR |
|----------|--------|-----|
| Cloud platform | Microsoft Azure | [ADR-0006](../architecture/decisions/0006-azure-cloud-platform.md) |
| Orchestration framework | LangGraph state machine | [ADR-0002](../architecture/decisions/0002-pipeline-orchestration.md) |
| Capability execution | Parallel domain processing | [ADR-0003](../architecture/decisions/0003-parallel-capability-execution.md) |
| Intelligence architecture | Layered capability model | [ADR-0001](../architecture/decisions/0001-layered-intelligence-architecture.md) |
| Public repository | Documentation-first | [ADR-0004](../architecture/decisions/0004-documentation-first-repository.md) |
| Domain analysis platform | Qwen model family | [ADR-0005](../architecture/decisions/0005-domain-analysis-platform.md) |

---

## Application Layer

| Component | Technology | Rationale |
|-----------|------------|-----------|
| Web client | React | Component-based SPA for assessment workflows |
| API gateway | Flask | Lightweight, proven Python web framework |
| Runtime | Python 3.11+ | Ecosystem alignment with intelligence tooling |

---

## Data Layer

| Component | Technology | Rationale |
|-----------|------------|-----------|
| Primary store | PostgreSQL | Relational integrity for assessment records |
| Cache | Redis | Low-latency external API response caching |

---

## Infrastructure Layer

| Component | Technology | Rationale |
|-----------|------------|-----------|
| Containers | Docker | Portable, consistent deployment units |
| Cloud | Microsoft Azure | Managed services, enterprise compliance |
| Secrets | Azure Key Vault | Centralized secrets management |
| Monitoring | Azure Monitor | Integrated observability |

---

## Integration Layer

| Integration | Purpose |
|-------------|---------|
| NASA POWER | Climate and meteorological enrichment |
| CHIRPS | High-resolution precipitation data |

→ Details: [integrations.md](./integrations.md)

---

## What Is Not Documented Here

Internal model configurations, prompt engineering, proprietary classification parameters, and production deployment manifests are maintained privately.
