# CI/CD Pipeline Design

Replaced legacy Jenkins with a GitHub Actions-based pipeline in Q3 2023.

## Pipeline Overview

```
Developer pushes code
        │
        ▼
  GitHub Actions triggered
        │
        ├─── Lint & Unit Tests  (parallel)
        ├─── Security Scan (Trivy, Checkov)
        │
        ▼
  Build Docker Image
        │
        ▼
  Push to Amazon ECR
        │
        ▼
  Deploy to Staging (auto)
        │
        ▼
  Integration Tests
        │
        ▼
  Manual approval gate ──► Deploy to Production
```

## Key Design Decisions

- **Reusable workflows:** Shared `.github/workflows/` templates used across 12 repos
- **Environment parity:** Staging and prod use identical Helm charts, different `values.yaml`
- **Rollback:** Automated rollback triggered if health checks fail post-deploy
- **Deploy time:** Average 12 minutes (down from ~2 hours with Jenkins)

## Tools Used

- GitHub Actions (orchestration)
- Docker + ECR (image build & registry)
- Helm (Kubernetes deployments)
- Terraform Cloud (infrastructure changes — separate pipeline)
- Slack notifications on deploy status
