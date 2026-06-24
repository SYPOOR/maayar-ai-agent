# Operational Considerations

Non-functional requirements, resilience patterns, and operational practices.

---

## Availability & Resilience

| Pattern | Implementation |
|---------|----------------|
| Multi-instance deployment | Container Apps with health checks |
| Stateless API | Horizontal scaling without session affinity |
| Session recovery | Assessment Core checkpoints in persistent store |
| Graceful degradation | Partial capability results with confidence adjustment |
| Circuit breaking | External API failure isolation |

---

## Performance Targets

| Metric | Target | Bottleneck |
|--------|--------|------------|
| Assessment intake | < 1 second | Input validation |
| Intelligence processing | 5–30 seconds | External API latency |
| Classification | 1–3 seconds | Synthesis computation |
| Report delivery | < 1 second | Persistence write |

---

## Observability

```
  Application Services
       │
       ├──▶ Metrics (Azure Monitor)
       │     · assessment.duration
       │     · capability.failure_rate
       │     · api.error_rate
       │
       ├──▶ Logs (Log Analytics)
       │     · Structured JSON with session_id
       │     · Lifecycle event logging
       │
       └──▶ Alerts
             · capability.failure_rate > 10% / 5min
             · assessment.abort_rate > 5% / 5min
             · external_api.latency.p95 > 30s
```

---

## Error Handling Posture

| Category | Response |
|----------|----------|
| Invalid intake | Reject with validation message |
| Capability timeout | Retry, then degrade with partial flag |
| All capabilities fail | Abort assessment with error |
| Infrastructure failure | Return retry guidance; session recoverable |

→ Workflow: [../workflows/operational-workflows.md](../workflows/operational-workflows.md)

---

## Security Operations

| Practice | Description |
|----------|-------------|
| Secrets rotation | Managed via Azure Key Vault policies |
| Access control | Role-based API authentication |
| Audit logging | All assessment events persisted |
| Data isolation | Customer data segregated by tenant |
| Vulnerability management | Container image scanning in ACR |

→ Security policy: [../SECURITY.md](../SECURITY.md)

---

## Capacity Planning

| Component | Scaling Trigger |
|-----------|-----------------|
| API Gateway | Request volume / CPU utilization |
| Intelligence Pipeline | Concurrent assessment count |
| PostgreSQL | Connection pool / storage growth |
| Redis | Memory utilization / cache hit ratio |
| External APIs | Rate limit proximity |
