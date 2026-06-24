# Decision Support Layer

Architecture of composite risk output and decision support delivery.

---

## Purpose

The Decision Support Layer produces the **final assessment output** consumed by stakeholders — a composite risk indicator with dimensional decomposition, confidence metadata, and audit-ready provenance.

---

## Output Model

```
  Classification Result
       │
       ▼
  ┌─────────────────────────┐
  │ Composite Risk Index    │  Single normalized risk indicator
  └────────────┬────────────┘
               │
       ┌───────┴───────┐
       ▼               ▼
  ┌──────────┐   ┌──────────────┐
  │ Tier     │   │ Dimensional  │
  │ Badge    │   │ Breakdown    │
  └──────────┘   └──────────────┘
       │               │
       ▼               ▼
  ┌──────────┐   ┌──────────────┐
  │Confidence│   │ Top Risk     │
  │ Indicator│   │ Factors      │
  └──────────┘   └──────────────┘
```

---

## Output Components

| Component | Description |
|-----------|-------------|
| **Composite Risk Index** | Normalized score for cross-farm comparison |
| **Risk Tier** | Categorical classification (Low → Critical) |
| **Dimensional Breakdown** | Per-capability contribution to composite score |
| **Top Risk Factors** | Ranked list of highest-impact factors |
| **Confidence Band** | Reflects data quality and capability participation |
| **Provenance Metadata** | Data sources, timestamps, assessment version |
| **Partial Flag** | Indicates degraded assessment when applicable |

---

## Stakeholder Interpretation

| Stakeholder | Primary Use |
|-------------|-------------|
| Farm operator | Prioritize interventions and resource allocation |
| Agronomist | Identify domains requiring deeper analysis |
| Insurer | Portfolio aggregation and underwriting support |
| Investor | Due diligence quantification |
| Policymaker | Regional risk mapping |

---

## Report Composition

Assessment reports delivered through the Presentation Layer include:

| Section | Source |
|---------|--------|
| Composite risk header | Decision Support output |
| Domain breakdown chart | Dimensional decomposition |
| Factor ranking | Classification contributing factors |
| Capability summaries | Individual domain signal highlights |
| Provenance panel | Data source attribution |
| Assessment metadata | Session ID, timestamps, partial flags |

---

## Auditability

Every decision support output supports full traceability:

1. Which capability domains contributed signals
2. Per-domain contribution to composite score
3. Highest-impact individual factors
4. Whether assessment was complete or partial
5. Data sources and freshness for each domain

→ Report workflow: [../workflows/decision-support-workflow.md](../workflows/decision-support-workflow.md)  
→ Screenshots: [../screenshots/reports/README.md](../screenshots/reports/README.md)
