# Operational Workflows

Error handling, degradation, monitoring, and recovery workflows.

---

## Error Classification

| Category | Severity | Response |
|----------|----------|----------|
| Input validation failure | Fatal | Reject request |
| Capability timeout | Degraded | Retry, then continue without |
| Capability failure | Degraded | Flag partial assessment |
| Classification failure | Fatal | Abort with error |
| Infrastructure failure | Fatal | Return retry guidance |

---

## Degradation Workflow

```
  Capability Failure
       │
       ▼
  Retries Remaining? ──Yes──▶ Retry Capability
       │ No
       ▼
  Mark Capability Degraded
       │
       ▼
  Minimum Capabilities Met? ──No──▶ Abort Assessment
       │ Yes
       ▼
  Continue Pipeline (partial: true)
       │
       ▼
  Adjust Confidence Downward
       │
       ▼
  Include Partial Notice in Report
```

---

## Monitoring Workflow

| Event | Action |
|-------|--------|
| Assessment started | Log session_id, farm_id, timestamp |
| Capability completed | Log capability_id, duration, signal_strength |
| Capability failed | Log error, retry count, degradation decision |
| Assessment completed | Log composite index, tier, duration |
| Assessment aborted | Log abort reason, failed stage |

---

## Recovery Workflow

| Scenario | Recovery |
|----------|----------|
| Mid-pipeline infrastructure failure | Resume from Assessment Core checkpoint |
| External API outage | Use cached data; degrade if unavailable |
| Database unavailable | Return service unavailable; no data loss (queued retry) |

→ Operations: [../architecture/operational-considerations.md](../architecture/operational-considerations.md)
