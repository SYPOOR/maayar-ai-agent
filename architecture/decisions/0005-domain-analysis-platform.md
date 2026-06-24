# ADR-0005: Domain Analysis Platform Selection

## Status

Accepted

## Context

The Intelligence Layer requires capable domain analysis for orchestration decisions and spatial data interpretation. Platform selection must balance capability, deployment flexibility, and data governance.

## Decision

We will deploy the **Qwen model family** for domain analysis within the Intelligence Layer, with self-hosted inference on cloud GPU infrastructure.

Specific model roles and configurations are maintained in the private production repository.

## Consequences

### Positive

- Strong multilingual capabilities for global agriculture
- Self-hosted deployment enables data sovereignty
- Open-weight platform reduces API dependency

### Negative

- GPU infrastructure management required
- Model updates require internal validation

## Alternatives Considered

| Alternative | Reason Not Selected |
|-------------|---------------------|
| Third-party API models | Data residency and cost at scale |
| Alternative open models | Weaker spatial analysis capabilities |

## References

- [Technology Decisions](../../technology/technology-decisions.md)

> **Note:** This ADR documents the platform selection decision only. Model configurations, prompt engineering, and inference parameters are not published.
