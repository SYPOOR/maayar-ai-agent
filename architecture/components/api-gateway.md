# API Gateway

External REST interface for the Maayar platform.

---

## Responsibilities

| Responsibility | Description |
|----------------|-------------|
| Request routing | Map endpoints to pipeline operations |
| Authentication | Token validation and access control |
| Validation | Input schema verification |
| Rate limiting | Request throttling via cache layer |
| Error handling | Standardized HTTP error responses |

---

## Integration

```
  Web Application ──▶ API Gateway ──▶ Assessment Core
                         │
                         ├── Data Platform
                         └── Cache Layer
```
