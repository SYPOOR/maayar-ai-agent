# Data Store

Persistent storage component within the Data Platform Layer.

---

## Storage Components

| Store | Technology | Purpose |
|-------|------------|---------|
| **Primary database** | PostgreSQL | Farm profiles, assessments, audit logs, checkpoints |
| **Cache** | Redis | API response cache, session state, rate limiting |

---

## Data Domains

| Domain | Description |
|--------|-------------|
| Farms | Farm configuration and boundary data |
| Assessments | Assessment sessions and lifecycle status |
| Domain signals | Capability output records |
| Risk outputs | Classification and decision support results |
| Audit logs | Lifecycle event history |

> Schema details are conceptual. Production schema is maintained privately.

→ [Data Platform](../../technology/data-platform.md)
