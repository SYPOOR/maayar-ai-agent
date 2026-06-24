# Platform Architecture

Layered architecture specification for the Maayar platform.

---

## Architecture Model

Maayar follows a **five-layer architecture** with an embedded Risk Intelligence Pipeline comprising four processing stages.

---

## System Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         PRESENTATION LAYER                              │
│                                                                         │
│   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐   ┌───────────┐  │
│   │ Dashboard   │   │ Assessment  │   │ Risk Report │   │ Portfolio │  │
│   │ Views       │   │ Workflow    │   │ Viewer      │   │ Overview  │  │
│   └─────────────┘   └─────────────┘   └─────────────┘   └───────────┘  │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │ HTTPS
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                          API GATEWAY LAYER                              │
│                                                                         │
│   Request Validation  ·  Authentication  ·  Rate Limiting  ·  Routing     │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                       RISK INTELLIGENCE PIPELINE                        │
│                                                                         │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Stage 1: DATA ACQUISITION LAYER                                  │   │
│  │  User context · Farm profiles · External API enrichment        │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  ▼                                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Stage 2: INTELLIGENCE LAYER                                      │   │
│  │  Orchestration · Parallel capability execution · Signal assembly │   │
│  │                                                                  │   │
│  │  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐  │   │
│  │  │Geospatial  │ │Crop Context│ │Operational │ │Disease     │  │   │
│  │  │Analysis    │ │Analysis    │ │Readiness   │ │Exposure    │  │   │
│  │  └────────────┘ └────────────┘ └────────────┘ └────────────┘  │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  ▼                                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Stage 3: ASSESSMENT CORE                                         │   │
│  │  Lifecycle management · Session state · Result assembly          │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  ▼                                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Stage 4: CLASSIFICATION SERVICES                                 │   │
│  │  Signal normalization · Domain weighting · Tier assignment       │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  ▼                                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Stage 5: DECISION SUPPORT LAYER                                  │   │
│  │  Composite risk output · Dimensional decomposition · Reporting   │   │
│  └──────────────────────────────────────────────────────────────────┘   │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                         DATA PLATFORM LAYER                             │
│                                                                         │
│   ┌─────────────────┐   ┌─────────────────┐   ┌─────────────────────┐  │
│   │ Persistent Store│   │ Cache Layer     │   │ External Integrations│  │
│   │ (PostgreSQL)    │   │ (Redis)         │   │ (NASA POWER, CHIRPS)│  │
│   └─────────────────┘   └─────────────────┘   └─────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Layer Responsibilities

| Layer | Responsibility | Key Concern |
|-------|----------------|-------------|
| **Presentation** | User interaction, visualization | UX, report rendering |
| **API Gateway** | External interface, access control | Security, validation |
| **Data Acquisition** | Data ingestion and enrichment | Source integration, caching |
| **Intelligence** | Domain analysis orchestration | Capability execution, parallelism |
| **Assessment Core** | Assessment lifecycle | State management, assembly |
| **Classification Services** | Risk synthesis | Normalization, tiering |
| **Decision Support** | Output delivery | Decomposition, confidence |
| **Data Platform** | Persistence and integration | Durability, performance |

---

## Interface Boundaries

Each layer communicates through **defined contracts**:

| Boundary | Contract Type |
|----------|---------------|
| Presentation ↔ API Gateway | REST API (assessment, report, farm resources) |
| API Gateway ↔ Assessment Core | Internal assessment commands |
| Data Acquisition ↔ External APIs | Integration adapters with caching |
| Intelligence ↔ Capabilities | Capability invocation with context payload |
| Capabilities ↔ Classification Services | Standardized domain signal objects |
| Classification ↔ Decision Support | Classified risk with decomposition metadata |

→ Output contract: [../capabilities/output-contract.md](../capabilities/output-contract.md)

---

## Non-Functional Architecture

| Requirement | Architectural Response |
|-------------|------------------------|
| Availability | Multi-instance deployment with health checks |
| Scalability | Stateless API; parallel capability execution |
| Latency | Cache layer for external data; parallel processing |
| Auditability | Structured logging; persistent assessment history |
| Security | Gateway authentication; secrets management |
| Recoverability | Session state persistence; checkpoint recovery |

→ Operations: [operational-considerations.md](./operational-considerations.md)
