# Infrastructure

Cloud infrastructure and container deployment.

---

## Infrastructure Overview

| Component | Service | Purpose |
|-----------|---------|---------|
| Edge | Azure Front Door | Load balancing, WAF, TLS |
| CDN | Azure CDN | Static asset delivery |
| Compute | Azure Container Apps | API and pipeline services |
| Registry | Azure Container Registry | Container images |
| Secrets | Azure Key Vault | Configuration management |
| Monitoring | Azure Monitor | Metrics, logs, alerts |

---

## Container Architecture

| Container | Contents |
|-----------|----------|
| `maayar-api` | API Gateway + Assessment Core + Pipeline |
| `maayar-web` | Web application (static build) |

---

## Environment Topology

| Environment | Purpose |
|-------------|---------|
| Development | Engineering iteration |
| Staging | Pre-production validation |
| Production | Live platform |

→ Deployment: [../architecture/deployment-topology.md](../architecture/deployment-topology.md)

---

## Security Controls

| Control | Implementation |
|---------|----------------|
| Network isolation | Azure Virtual Network |
| Identity | Managed service identities |
| Secrets | Key Vault (no secrets in images) |
| Encryption | TLS in transit; encryption at rest |
| WAF | Azure Front Door rules |
