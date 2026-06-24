# Technology Stack Overview

Technology stack organized by architectural layer.

---

## Stack by Layer

| Layer | Technology | Role |
|-------|------------|------|
| **Presentation** | React | Single-page web application |
| **API** | Flask | REST API gateway |
| **Intelligence** | LangGraph | Pipeline orchestration state machine |
| **Intelligence** | Qwen 3 | Domain reasoning and orchestration |
| **Intelligence** | Qwen 2.5 VL | Spatial and visual analysis |
| **Data** | PostgreSQL | Persistent storage |
| **Data** | Redis | Cache and session state |
| **Infrastructure** | Docker | Container runtime |
| **Infrastructure** | Microsoft Azure | Cloud platform |
| **Integrations** | NASA POWER API | Climate and solar data |
| **Integrations** | CHIRPS API | Precipitation data |

---

## Layer Mapping

```
  React ──────▶ Flask ──────▶ Intelligence Pipeline ──────▶ PostgreSQL
                                  │                            Redis
                                  ▼
                            External APIs
                            (NASA POWER, CHIRPS)
```

---

## Technology Selection Criteria

| Criterion | Application |
|-----------|-------------|
| Maturity | Production-proven technologies preferred |
| Scalability | Horizontal scaling for stateless components |
| Operability | Managed services to reduce operational burden |
| Data sovereignty | Self-hosted intelligence where required |
| Integration | Standard APIs for external data sources |

→ Decisions: [technology-decisions.md](./technology-decisions.md)
