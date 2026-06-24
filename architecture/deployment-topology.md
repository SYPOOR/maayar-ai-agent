# Deployment Topology

Cloud deployment architecture for the Maayar platform on Microsoft Azure.

---

## Deployment Diagram

```
                        ┌──────────────┐
                        │    Users     │
                        └──────┬───────┘
                               │ HTTPS
                               ▼
                   ┌───────────────────────┐
                   │   Azure Front Door    │
                   │   (WAF + Routing)     │
                   └───────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              ▼                                 ▼
   ┌──────────────────┐              ┌──────────────────┐
   │  Azure CDN       │              │  Azure Container │
   │  (Static Assets) │              │  Apps            │
   │  Web Application │              │  API + Pipeline  │
   └──────────────────┘              └────────┬─────────┘
                                              │
                         ┌────────────────────┼────────────────────┐
                         ▼                    ▼                    ▼
              ┌──────────────────┐  ┌──────────────────┐  ┌──────────────┐
              │ Azure Database   │  │ Azure Cache      │  │ Azure Key    │
              │ for PostgreSQL   │  │ for Redis        │  │ Vault        │
              └──────────────────┘  └──────────────────┘  └──────────────┘
                                              │
                                              ▼
                                    ┌──────────────────┐
                                    │ Azure Monitor    │
                                    │ + Log Analytics  │
                                    └──────────────────┘
```

---

## Azure Services

| Service | Role |
|---------|------|
| **Azure Front Door** | Global load balancing, WAF, TLS termination |
| **Azure CDN** | Static asset delivery for web application |
| **Azure Container Apps** | API Gateway and Risk Intelligence Pipeline |
| **Azure Database for PostgreSQL** | Persistent data store |
| **Azure Cache for Redis** | Cache and session state |
| **Azure Container Registry** | Container image management |
| **Azure Key Vault** | Secrets and configuration management |
| **Azure Monitor** | Metrics, logs, alerting |

---

## Environment Strategy

| Environment | Purpose | Scale |
|-------------|---------|-------|
| **Development** | Engineering iteration | Minimal shared resources |
| **Staging** | Pre-production validation | Production mirror (reduced) |
| **Production** | Live platform | Full topology |

---

## Security Architecture

| Control | Implementation |
|---------|----------------|
| Network isolation | Azure Virtual Network |
| Service authentication | Managed identities |
| Secrets management | Azure Key Vault (no secrets in containers) |
| Edge protection | Azure Front Door WAF |
| Encryption | TLS 1.2+ in transit; encryption at rest |

→ Technology: [../technology/infrastructure.md](../technology/infrastructure.md)  
→ ADR: [decisions/0006-azure-cloud-platform.md](./decisions/0006-azure-cloud-platform.md)
