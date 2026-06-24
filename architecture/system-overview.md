# System Overview

High-level overview of the Maayar Agricultural Risk Intelligence Platform.

---

## Platform Context

```
┌──────────────┐         ┌──────────────────────────────┐         ┌──────────────┐
│   Farm       │         │                              │         │   External   │
│   Operators  │────────▶│   Maayar Platform            │◀────────│   Data APIs  │
│   Analysts   │         │   Agricultural Risk          │         │   NASA POWER │
│   Insurers   │◀────────│   Intelligence               │         │   CHIRPS     │
└──────────────┘         └──────────────────────────────┘         └──────────────┘
                                      │
                                      ▼
                           ┌──────────────────┐
                           │  Microsoft Azure │
                           │  (Cloud Platform) │
                           └──────────────────┘
```

---

## Problem Statement

Agricultural risk is inherently multidimensional. Effective risk assessment requires synthesizing environmental conditions, crop-specific factors, operational readiness, and disease exposure — each drawing from distinct data sources and analytical approaches.

Traditional approaches either oversimplify risk into single metrics or depend on manual expert analysis that does not scale across portfolios.

---

## Platform Solution

Maayar provides a **structured risk intelligence pipeline** that:

1. Acquires and enriches multi-source data for a given farm context
2. Executes parallel domain analysis across four capability areas
3. Synthesizes capability outputs through Classification Services
4. Delivers composite risk assessments via the Decision Support Layer

---

## Core Platform Capabilities

| Capability | Description |
|------------|-------------|
| **Farm Assessment** | End-to-end risk evaluation for individual farms |
| **Dimensional Decomposition** | Per-domain risk contribution breakdown |
| **Portfolio Intelligence** | Aggregated risk views across multiple farms |
| **Decision Support Output** | Tiered risk classification with confidence indicators |
| **Audit Trail** | Traceable data provenance and assessment history |

---

## Stakeholder Value

| Stakeholder | Value Delivered |
|-------------|-----------------|
| Farm operators | Actionable risk intelligence for operational planning |
| Agronomists | Structured domain analysis replacing ad-hoc assessment |
| Insurers | Standardized risk metrics for underwriting support |
| Investors | Quantified due diligence for agricultural assets |
| Policymakers | Regional risk visibility for food security planning |

---

## Architectural Posture

Maayar is designed as an **enterprise intelligence platform**, not a single-model application. Architecture emphasizes:

- Defined layer boundaries with explicit interfaces
- Domain capability modules with standardized output contracts
- Documented technology decisions with ADR governance
- Cloud-native deployment with operational observability

→ Detailed architecture: [platform-architecture.md](./platform-architecture.md)
