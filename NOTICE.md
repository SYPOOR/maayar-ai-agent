# Public Repository Notice

**Document Classification:** Public Architecture & Engineering Documentation  
**Platform:** Maayar — Agricultural Risk Intelligence Platform  
**Effective Date:** June 2025

---

## Purpose

This repository is the designated **public engineering documentation surface** for the Maayar platform. It exists to communicate architectural intent, system design maturity, and product engineering discipline to technical evaluators, investors, partners, and the broader engineering community.

This repository answers three questions:

1. **What** does the Maayar platform do?
2. **How** is the platform architected?
3. **How** does information flow through the system?

It does not answer how proprietary logic, internal models, or production implementations are built.

---

## Contents of This Repository

| Category | Description |
|----------|-------------|
| **Architecture** | Layer design, component boundaries, deployment topology |
| **Capabilities** | Domain capability specifications and output contracts |
| **Workflows** | Assessment pipeline, data acquisition, decision support flows |
| **Product** | Vision, use cases, roadmap, value proposition |
| **Technology** | Stack overview, technology decisions, integration patterns |
| **Governance** | Contributing guidelines, security policy, ADRs |

---

## Excluded From This Repository

The following categories are **intentionally maintained outside** this public repository:

| Category | Rationale |
|----------|-----------|
| Production source code | Intellectual property protection; controlled release cadence |
| Proprietary classification logic | Competitive differentiation in risk modeling |
| Internal model configurations | Operational security and IP protection |
| Prompt and inference artifacts | Prevents replication of proprietary behavior |
| API keys, credentials, secrets | Security compliance |
| Production deployment manifests | Operational security |
| Customer data and farm records | Privacy and regulatory compliance |
| Training data and model weights | Data governance and IP protection |

---

## Public and Private Surfaces

```
┌────────────────────────────────────────────────────────────────────┐
│                        MAAYAR PLATFORM                              │
├──────────────────────────────┬─────────────────────────────────────┤
│     PUBLIC (This Repo)       │     PRIVATE (Production)             │
├──────────────────────────────┼─────────────────────────────────────┤
│  Architecture documentation  │  Application implementations         │
│  Capability specifications   │  Classification algorithms           │
│  Workflow definitions        │  Model configurations                │
│  Technology decisions        │  Deployment configurations           │
│  ADRs and design artifacts   │  Operational infrastructure          │
│  Product vision and roadmap  │  Customer environments               │
│  Diagrams and screenshots    │  Proprietary data pipelines          │
└──────────────────────────────┴─────────────────────────────────────┘
```

Architectural documentation in this repository reflects **production design intent**. Implementation details remain private unless explicitly released through authorized channels.

---

## Intellectual Property

All architecture concepts, system designs, workflow specifications, capability definitions, and documentation contained herein are the intellectual property of the Maayar project maintainers.

Documentation is provided for **review, evaluation, partnership assessment, and educational purposes**. Unauthorized reproduction of proprietary implementation details derived from private systems is prohibited.

---

## For Technical Evaluators

When reviewing Maayar through this repository:

| Signal | Indicator |
|--------|-----------|
| **Architectural maturity** | Layered design, defined boundaries, documented ADRs |
| **Engineering discipline** | Structured workflows, output contracts, operational considerations |
| **Product clarity** | Defined use cases, capability domains, decision support model |
| **IP posture** | Deliberate separation of public design and private implementation |

The absence of source code is a **documented architectural publishing strategy** (see [ADR-0004](./architecture/decisions/0004-documentation-first-repository.md)), not an indicator of project immaturity.

For diligence beyond this repository, contact maintainers through established project channels.

---

## Amendments

This notice may be updated as the platform matures. Material changes are recorded in [CHANGELOG.md](./CHANGELOG.md).
