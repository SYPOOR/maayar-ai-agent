# Security Policy

## Supported Versions

This repository contains documentation only. Security updates apply to the private production implementation, not to files in this repository.

| Surface | Scope |
|---------|-------|
| This repository | Public documentation and design artifacts |
| Production platform | Private — contact maintainers for security disclosures |

---

## Reporting a Vulnerability

If you discover a security vulnerability related to Maayar's **production systems**, **public API surfaces**, or **disclosed architecture** that could lead to exploitation:

**Please do not open a public GitHub issue.**

Instead, report responsibly by contacting the maintainers through your established project correspondence channel.

Include:

- Description of the vulnerability
- Steps to reproduce (if applicable)
- Potential impact assessment
- Any suggested remediation (optional)

We aim to acknowledge reports within **5 business days** and provide a status update within **14 business days**.

---

## Scope

### In Scope

- Security issues in publicly described API contracts
- Architecture disclosures that reveal exploitable attack surfaces
- Documentation that inadvertently exposes credentials or secrets

### Out of Scope

- Social engineering attacks
- Denial of service against documentation hosting
- Issues in third-party services (NASA POWER, CHIRPS, Azure) — report to those vendors directly
- Vulnerabilities requiring access to private production systems

---

## Documentation Security

When contributing documentation:

- **Never** commit API keys, tokens, passwords, or `.env` files
- **Never** include production URLs with embedded credentials
- **Never** expose internal network topology beyond architectural abstractions
- Use placeholder values for all configuration examples

---

## Recognition

We appreciate responsible disclosure and will acknowledge researchers who report valid vulnerabilities (with permission).
