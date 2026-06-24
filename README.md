<div align="center">

# Maayar

### Agricultural Risk Intelligence Platform

[![Documentation](https://img.shields.io/badge/docs-architecture-0A5C36)](./docs/README.md)
[![License](https://img.shields.io/badge/license-documentation-lightgrey)](./LICENSE)
[![Status](https://img.shields.io/badge/status-active%20development-0A5C36)]()

*Enterprise-grade agricultural risk intelligence — architected for decision support at scale.*

[Architecture](./architecture/README.md) · [Capabilities](./capabilities/README.md) · [Workflows](./workflows/README.md) · [Product](./product/README.md) · [Technology](./technology/README.md)

</div>

---

## Repository Notice

> This repository publishes **architecture documentation, system design artifacts, and engineering specifications** for the Maayar platform. Production implementations, proprietary components, and operational configurations remain private.
>
> Full notice: [NOTICE.md](./NOTICE.md)

---

## 1. Platform Overview

**Maayar** is an agricultural risk intelligence platform that transforms multi-source environmental, operational, and agronomic data into structured risk assessments for farms and agricultural portfolios.

The platform is organized as a **layered intelligence architecture** with clear separation between data acquisition, domain analysis, assessment synthesis, and decision support — enabling auditable, scalable risk intelligence without exposing proprietary implementation details.

| Attribute | Description |
|-----------|-------------|
| **Domain** | Agricultural risk intelligence |
| **Architecture** | Layered intelligence with domain capability modules |
| **Deployment** | Cloud-native, containerized infrastructure |
| **Output** | Composite risk assessments with dimensional decomposition |
| **Audience** | Farm operators, agronomists, insurers, investors, policymakers |

---

## 2. Repository Scope

| Published in This Repository | Maintained Privately |
|------------------------------|----------------------|
| Platform architecture and layer design | Production source code |
| Capability domain specifications | Proprietary classification logic |
| Assessment and decision workflows | Internal model configurations |
| Technology decisions and ADRs | Operational secrets and credentials |
| Deployment topology (conceptual) | Customer data and telemetry |
| Product vision and use cases | Implementation-specific prompts |

→ Scope policy: [NOTICE.md](./NOTICE.md)

---

## 3. Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         PRESENTATION LAYER                              │
│              Web Application  ·  Reporting  ·  Portfolio Views          │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                           API GATEWAY LAYER                             │
│              Request Validation  ·  Authentication  ·  Routing            │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                      RISK INTELLIGENCE PIPELINE                           │
│                                                                           │
│   ┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐   │
│   │ Data Acquisition │───▶│  Intelligence    │───▶│  Assessment      │   │
│   │ Layer            │    │  Layer           │    │  Core            │   │
│   └──────────────────┘    └────────┬─────────┘    └────────┬─────────┘   │
│                                    │                       │             │
│                          ┌─────────┴─────────┐             │             │
│                          ▼         ▼         ▼             ▼             │
│                    ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────┐ │
│                    │Geospatial│ │ Crop    │ │Operational│ │Classification│ │
│                    │Analysis │ │ Context │ │ Readiness │ │ Services    │ │
│                    └─────────┘ └─────────┘ └─────────┘ └──────┬──────┘ │
│                                                                │         │
│                                                                ▼         │
│                                                    ┌──────────────────┐ │
│                                                    │ Decision Support │ │
│                                                    │ Layer            │ │
│                                                    └──────────────────┘ │
└─────────────────────────────────────────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                           DATA PLATFORM LAYER                             │
│         Persistent Store  ·  Cache  ·  External Data Integrations       │
└─────────────────────────────────────────────────────────────────────────┘
```

→ Full architecture: [architecture/platform-architecture.md](./architecture/platform-architecture.md)

---

## 4. Platform Components

| Component | Layer | Responsibility |
|-----------|-------|----------------|
| **Web Application** | Presentation | Assessment workflows, dashboards, report visualization |
| **API Gateway** | API | External interface, validation, access control |
| **Data Acquisition Layer** | Pipeline | External and user-provided data ingestion and enrichment |
| **Intelligence Layer** | Pipeline | Domain capability orchestration and signal generation |
| **Assessment Core** | Pipeline | Assessment lifecycle management and result assembly |
| **Classification Services** | Pipeline | Risk normalization, weighting, and tier assignment |
| **Decision Support Layer** | Pipeline | Composite risk output and dimensional decomposition |
| **Data Platform** | Infrastructure | Persistence, caching, and integration services |

→ Component specifications: [architecture/README.md](./architecture/README.md)

---

## 5. Assessment Workflow

```
  User Request
       │
       ▼
  ┌─────────┐     ┌─────────────────┐     ┌─────────────────────┐
  │ Intake  │────▶│ Data Acquisition │────▶│ Intelligence        │
  │         │     │ & Enrichment     │     │ Orchestration       │
  └─────────┘     └─────────────────┘     └──────────┬──────────┘
                                                       │
                         ┌─────────────────────────────┼─────────────────────────────┐
                         ▼              ▼              ▼              ▼               │
                   Geospatial     Crop Context   Operational    Disease Exposure      │
                   Analysis       Analysis       Readiness      Analysis              │
                         │              │              │              │               │
                         └──────────────┴──────────────┴──────────────┘               │
                                                       │                               │
                                                       ▼                               │
                                            ┌─────────────────────┐                  │
                                            │ Classification       │                  │
                                            │ Services             │                  │
                                            └──────────┬──────────┘                  │
                                                       │                               │
                                                       ▼                               │
                                            ┌─────────────────────┐                  │
                                            │ Decision Support     │                  │
                                            │ Output               │                  │
                                            └──────────┬──────────┘                  │
                                                       │                               │
                                                       ▼                               │
                                                 Assessment Report                    │
```

| Phase | Description | Documentation |
|-------|-------------|---------------|
| **Intake** | Farm context capture and validation | [Risk Assessment Pipeline](./workflows/risk-assessment-pipeline.md) |
| **Acquisition** | External data enrichment | [Data Acquisition Strategy](./workflows/data-acquisition-strategy.md) |
| **Intelligence** | Parallel domain analysis | [Intelligence Orchestration](./workflows/intelligence-orchestration.md) |
| **Classification** | Risk synthesis and tiering | [Decision Support Workflow](./workflows/decision-support-workflow.md) |
| **Delivery** | Report generation and persistence | [Operational Workflows](./workflows/operational-workflows.md) |

---

## 6. Capability Domains

Maayar's Intelligence Layer comprises four **capability domains**, each responsible for a distinct dimension of agricultural risk.

| Capability Domain | Risk Dimension | Primary Inputs |
|-------------------|------------------|----------------|
| [Geospatial Analysis](./capabilities/geospatial-intelligence.md) | Environmental and climate exposure | Climate APIs, precipitation data, spatial boundaries |
| [Crop Context Analysis](./capabilities/crop-context-analysis.md) | Crop-specific phenological risk | Crop calendars, regional suitability data |
| [Operational Readiness](./capabilities/operational-readiness.md) | Farm preparedness and infrastructure | Farm profiles, readiness indicators |
| [Disease Exposure Analysis](./capabilities/disease-exposure-analysis.md) | Pathogen and pest pressure | Climate correlation, regional disease indices |

```
                    ┌─────────────────────────┐
                    │  Intelligence Layer     │
                    │  (Orchestration)          │
                    └────────────┬────────────┘
                                 │
           ┌─────────────────────┼─────────────────────┐
           │                     │                     │
           ▼                     ▼                     ▼
   ┌───────────────┐    ┌───────────────┐    ┌───────────────┐
   │  Geospatial   │    │  Crop Context │    │  Operational  │
   │  Analysis     │    │  Analysis     │    │  Readiness    │
   └───────────────┘    └───────────────┘    └───────────────┘
                                 │
                                 ▼
                    ┌───────────────┐
                    │  Disease      │
                    │  Exposure     │
                    │  Analysis     │
                    └───────────────┘
```

→ Capability catalog: [capabilities/README.md](./capabilities/README.md)

---

## 7. Technology Landscape

| Layer | Technologies |
|-------|-------------|
| **Application** | Web framework (API), modern SPA (client) |
| **Intelligence** | Orchestration framework, domain analysis services |
| **Data** | Relational database, in-memory cache |
| **Infrastructure** | Container runtime, cloud platform (Microsoft Azure) |
| **Integrations** | NASA POWER API, CHIRPS precipitation API |

→ Technology decisions: [technology/technology-decisions.md](./technology/technology-decisions.md)  
→ Stack overview: [technology/stack-overview.md](./technology/stack-overview.md)

---

## 8. Documentation Index

| Section | Description |
|---------|-------------|
| [architecture/](./architecture/README.md) | Platform architecture, layers, components, ADRs |
| [capabilities/](./capabilities/README.md) | Domain capability specifications |
| [workflows/](./workflows/README.md) | Assessment, acquisition, and decision workflows |
| [product/](./product/README.md) | Vision, use cases, roadmap |
| [technology/](./technology/README.md) | Stack, infrastructure, integrations |
| [docs/](./docs/README.md) | Onboarding guides and reference |
| [screenshots/](./screenshots/README.md) | Platform interface captures |
| [assets/](./assets/README.md) | Brand and diagram exports |

### Recommended Reading Paths

| Audience | Start Here | Time |
|----------|------------|------|
| **Evaluators & Judges** | [docs/getting-started/for-evaluators.md](./docs/getting-started/for-evaluators.md) | 15 min |
| **Architects & CTOs** | [docs/getting-started/for-architects.md](./docs/getting-started/for-architects.md) | 30 min |
| **Investors** | [docs/getting-started/for-investors.md](./docs/getting-started/for-investors.md) | 10 min |

---

## 9. Repository Notice

This is an **Architecture & Engineering Documentation Repository**.

It is designed to communicate system design maturity, architectural intent, and product engineering discipline. It is not a source code distribution. Production systems, proprietary logic, and operational configurations are maintained separately under controlled access.

→ [NOTICE.md](./NOTICE.md) · [CONTRIBUTING.md](./CONTRIBUTING.md) · [SECURITY.md](./SECURITY.md)

---

## 10. Team Information

| Role | Responsibility |
|------|----------------|
| **Platform Architecture** | System design, layer boundaries, ADR governance |
| **Intelligence Engineering** | Capability domain design and orchestration patterns |
| **Product Engineering** | Assessment workflows, decision support output |
| **Infrastructure Engineering** | Cloud deployment, data platform, observability |

Maayar is developed by a cross-functional engineering team with expertise in agricultural systems, distributed architecture, and applied intelligence platforms.

For partnership, evaluation, or diligence inquiries, refer to [SECURITY.md](./SECURITY.md) and project correspondence channels.

---

<div align="center">

**Maayar** — *Precision intelligence for agricultural resilience.*

Documentation Repository · v0.2.0

</div>
