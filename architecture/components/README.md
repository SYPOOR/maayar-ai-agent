# Components

Component-level specifications within the Maayar layered architecture.

---

## Component Map

```
  Presentation Layer
  └── Web Application

  API Gateway Layer
  └── API Gateway Service

  Risk Intelligence Pipeline
  ├── Data Acquisition Service
  ├── Intelligence Orchestrator
  ├── Assessment Core
  ├── Classification Engine
  └── Decision Support Service

  Data Platform Layer
  ├── Persistent Store (PostgreSQL)
  ├── Cache Layer (Redis)
  └── Integration Adapters
```

---

## Component Index

| Component | Layer | Documentation |
|-----------|-------|---------------|
| [api-gateway.md](./api-gateway.md) | API Gateway | External REST interface |
| [web-client.md](./web-client.md) | Presentation | Web application |
| [pipeline-runtime.md](./pipeline-runtime.md) | Pipeline | Assessment Core + orchestration |
| [classification-engine.md](./classification-engine.md) | Pipeline | Classification Services |
| [data-store.md](./data-store.md) | Data Platform | PostgreSQL persistence |
| [cache-layer.md](./cache-layer.md) | Data Platform | Redis caching |

---

## Interaction Model

```
  Web Client ◀──▶ API Gateway ◀──▶ Pipeline Runtime
                                        │
                         ┌──────────────┼──────────────┐
                         ▼              ▼              ▼
                   Data Store      Cache Layer    Integrations
```
