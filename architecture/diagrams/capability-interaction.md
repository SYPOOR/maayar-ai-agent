# Capability Interaction Diagram

```
                    ┌─────────────────────────┐
                    │    Assessment Core      │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │   Intelligence Layer    │
                    │   (Orchestration)       │
                    └────────────┬────────────┘
                                 │
         ┌───────────┬───────────┼───────────┬───────────┐
         │           │           │           │           │
         ▼           ▼           ▼           ▼           │
  ┌────────────┐┌────────────┐┌────────────┐┌────────────┐
  │Geospatial  ││Crop Context││Operational ││Disease     │
  │Analysis    ││Analysis    ││Readiness   ││Exposure    │
  │            ││            ││            ││Analysis    │
  │ ┌────────┐ ││            ││            ││            │
  │ │NASA    │ ││            ││ ┌────────┐ ││ ┌────────┐ │
  │ │POWER   │ ││            ││ │Farm    │ ││ │Disease │ │
  │ │CHIRPS  │ ││            ││ │Profile │ ││ │Indices │ │
  │ └────────┘ ││            ││ └────────┘ ││ └────────┘ │
  └─────┬──────┘└─────┬──────┘└─────┬──────┘└─────┬──────┘
        │             │             │             │
        │   (No inter-capability communication)  │
        │             │             │             │
        └─────────────┴──────┬──────┴─────────────┘
                             │
                             ▼
                    ┌─────────────────────────┐
                    │  Domain Signal Assembly │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │  Classification Services│
                    └─────────────────────────┘
```

**Interaction rules:**
- Capabilities receive context from Intelligence Layer only
- Capabilities do not communicate with each other
- Each capability accesses its own data dependencies
- All outputs conform to the domain output contract
