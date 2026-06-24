# ADR-0003: Parallel Capability Execution

## Status

Accepted

## Context

Each assessment requires outputs from four domain capability modules. Sequential execution multiplies latency, particularly when capabilities depend on external API calls with seconds of latency.

## Decision

We will execute all domain capability modules **in parallel** within the Intelligence Layer, waiting for all to complete or timeout before proceeding to Classification Services.

## Consequences

### Positive

- Latency bounded by slowest capability, not sum
- Better resource utilization
- Improved user experience

### Negative

- Higher concurrent load on infrastructure and external APIs
- Partial failure handling more complex

## Alternatives Considered

| Alternative | Reason Not Selected |
|-------------|---------------------|
| Sequential execution | Unacceptable latency |
| Streaming partial results | Synthesis still requires all signals |

## References

- [Intelligence Orchestration](../intelligence-orchestration.md)
- [Assessment Workflow](../diagrams/assessment-workflow.md)
