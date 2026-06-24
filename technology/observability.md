# Observability

Monitoring, logging, and alerting for the Maayar platform.

---

## Observability Stack

| Component | Technology | Purpose |
|-----------|------------|---------|
| Metrics | Azure Monitor | Service health, latency, throughput |
| Logs | Azure Log Analytics | Structured application logs |
| Alerts | Azure Monitor Alerts | Threshold-based notifications |

---

## Key Metrics

| Metric | Alert Threshold |
|--------|-----------------|
| `assessment.duration.p95` | > 60 seconds |
| `capability.failure_rate` | > 10% / 5 minutes |
| `api.error_rate` | > 1% / 5 minutes |
| `external_api.latency.p95` | > 30 seconds |
| `pipeline.abort_rate` | > 5% / 5 minutes |

---

## Logging Standards

| Level | Usage |
|-------|-------|
| INFO | Assessment lifecycle events |
| WARN | Capability degradation, partial assessments |
| ERROR | Failures, infrastructure issues |

All logs include `session_id` and `assessment_id` for traceability.

---

## Audit Trail

Assessment audit events are persisted to PostgreSQL for long-term compliance, independent of operational log retention.

→ Operations: [../architecture/operational-considerations.md](../architecture/operational-considerations.md)
