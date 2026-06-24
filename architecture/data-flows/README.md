# Data Flows

Information flow documentation for the Maayar platform.

---

## Flow Index

| Flow | Documentation |
|------|---------------|
| [assessment-flow.md](./assessment-flow.md) | End-to-end assessment data movement |
| [acquisition-flow.md](./acquisition-flow.md) | External data acquisition path |
| [capability-output-flow.md](./capability-output-flow.md) | Capability signal to classification |
| [report-flow.md](./report-flow.md) | Decision support to presentation |

---

## Master Flow

```
  User Input ──▶ API Gateway ──▶ Assessment Core
                                      │
                    ┌─────────────────┼─────────────────┐
                    ▼                 ▼                 ▼
              Data Acquisition   Capabilities    Classification
                    │                 │                 │
                    └─────────────────┴─────────────────┘
                                      │
                                      ▼
                              Decision Support ──▶ Report
```
