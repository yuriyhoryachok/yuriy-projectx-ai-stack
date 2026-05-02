# Legacy Architecture (Pre-2023)

> Diagram description — visual diagrams (PNG/SVG) will be added to this folder.

## High-Level Overview

```
                  ┌─────────────────────────────────────────┐
                  │              AWS us-east-1              │
                  │                                         │
  Internet ──────►│  ALB (manually configured)              │
                  │    │                                     │
                  │    ├──► EC2: PayFlow App (t3.large) x2  │
                  │    │      (SSH-deployed, no containers)  │
                  │    │                                     │
                  │    └──► EC2: Admin Portal (t3.medium)   │
                  │                                         │
                  │  EC2: Jenkins (t3.medium, standalone)   │
                  │  EC2: PostgreSQL (db manually managed)  │
                  │  S3: Static assets (manually synced)    │
                  └─────────────────────────────────────────┘
```

## Tech Stack (Legacy)

- **Cloud:** AWS (no IaC — everything via Console or ad-hoc CLI)
- **CI/CD:** Jenkins (single node, jobs configured manually via UI)
- **Compute:** EC2 instances with `systemd` services
- **Database:** PostgreSQL on EC2 (no RDS, manual backups)
- **Secrets:** Plaintext in `/etc/app/.env` files on servers
- **Monitoring:** Basic CloudWatch alarms, no dashboards
