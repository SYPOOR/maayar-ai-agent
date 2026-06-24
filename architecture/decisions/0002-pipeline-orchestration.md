# ADR-0002: Pipeline Orchestration Framework

## Status

Accepted

## Context

The Risk Intelligence Pipeline requires multi-stage processing with conditional branching (capability failures, partial results, retries). Simple request-response patterns are insufficient for stateful workflows spanning data acquisition, parallel capability execution, and classification.

## Decision

We will use a **state machine orchestration framework** (LangGraph) for pipeline execution, with session checkpoints persisted to the Data Platform.

## Consequences

### Positive

- Explicit pipeline state modeling
- Checkpoint-based session recovery
- Conditional branching for degradation paths
- Industry-standard orchestration patterns

### Negative

- Additional framework dependency
- Checkpoint storage adds write overhead

## Alternatives Considered

| Alternative | Reason Not Selected |
|-------------|---------------------|
| Custom state machine | Higher maintenance burden |
| Workflow engines (Temporal) | Over-engineered for current scale |
| Simple async chain | No recovery, poor error handling |

## References

- [Assessment Core](../assessment-core.md)
- [Intelligence Orchestration](../intelligence-orchestration.md)
