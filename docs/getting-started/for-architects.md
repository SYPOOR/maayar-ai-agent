# For Architects

Technical onboarding for software architects and CTOs.

---

## 30-Minute Architecture Review

### 1. System Context (5 min)

- [System Overview](../architecture/system-overview.md)
- [Platform Context Diagram](../architecture/diagrams/platform-context.md)

### 2. Layered Architecture (10 min)

- [Platform Architecture](../architecture/platform-architecture.md)
- [Intelligence Orchestration](../architecture/intelligence-orchestration.md)
- [Assessment Core](../architecture/assessment-core.md)
- [Classification Services](../architecture/classification-services.md)
- [Decision Support Layer](../architecture/decision-support-layer.md)

### 3. Capabilities & Data (5 min)

- [Capability Catalog](../capabilities/README.md)
- [Output Contract](../capabilities/output-contract.md)
- [Data Acquisition Layer](../architecture/data-acquisition-layer.md)

### 4. Operations & Evolution (5 min)

- [Deployment Topology](../architecture/deployment-topology.md)
- [Operational Considerations](../architecture/operational-considerations.md)
- [Future Evolution](../architecture/future-evolution.md)

### 5. Decisions (5 min)

- [ADR Index](../architecture/decisions/README.md)

---

## Key Patterns

| Pattern | Implementation |
|---------|----------------|
| Layered intelligence | 5-layer architecture with embedded pipeline |
| Capability modularity | 4 independent domain modules with output contract |
| Parallel processing | Concurrent capability execution |
| Graceful degradation | Partial assessments with confidence adjustment |
| Documentation-first | Public design, private implementation |
