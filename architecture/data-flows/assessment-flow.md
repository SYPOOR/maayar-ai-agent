# Assessment Data Flow

```
  User ──▶ API Gateway ──▶ Assessment Core
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
        Data Acquisition   Capabilities   Classification
              │                │                │
              └────────────────┴────────────────┘
                               │
                               ▼
                        Decision Support
                               │
                               ▼
                        Data Platform (persist)
                               │
                               ▼
                        Web Application (report)
```
