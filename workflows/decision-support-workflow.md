# Decision Support Workflow

From classification result to stakeholder-facing assessment report.

---

## Decision Support Flow

```
  Domain Signals (from Intelligence Layer)
       │
       ▼
  ┌─────────────────────┐
  │ Classification      │
  │ Services            │
  │  · Normalize        │
  │  · Weight           │
  │  · Aggregate        │
  │  · Classify         │
  └─────────┬───────────┘
            │
            ▼
  ┌─────────────────────┐
  │ Decision Support    │
  │ Layer               │
  │  · Composite Index  │
  │  · Decomposition    │
  │  · Confidence       │
  └─────────┬───────────┘
            │
            ▼
  ┌─────────────────────┐
  │ Report Composition  │
  └─────────┬───────────┘
            │
            ▼
  ┌─────────────────────┐
  │ Presentation Layer  │
  │ (Report Rendering)  │
  └─────────────────────┘
```

---

## Report Sections

| Section | Content Source |
|---------|----------------|
| Composite risk header | Decision Support composite index + tier |
| Domain breakdown | Classification dimensional decomposition |
| Top risk factors | Classification contributing factors |
| Capability summaries | Individual domain signal highlights |
| Provenance panel | Capability provenance metadata |
| Assessment metadata | Session ID, timestamps, partial flags |

---

## Export Formats

| Format | Status |
|--------|--------|
| Interactive web report | Available |
| Machine-readable (JSON) | Available |
| PDF export | Planned |

→ Architecture: [../architecture/decision-support-layer.md](../architecture/decision-support-layer.md)
