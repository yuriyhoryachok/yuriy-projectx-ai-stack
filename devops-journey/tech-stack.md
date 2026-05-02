# Tech Stack Overview

Full comparison of the technology stack before and after my tenure at NovaTech Solutions.

## Side-by-Side Comparison

| Category | Before (Jan 2023) | After (2024) |
|---|---|---|
| **Cloud IaC** | None — AWS Console + ad-hoc CLI | Terraform (modules, remote state in S3) |
| **Compute** | EC2 + systemd | Amazon EKS (Kubernetes 1.29) |
| **CI/CD** | Jenkins (single EC2, manual config) | GitHub Actions (reusable workflows) |
| **Deployments** | SSH + bash scripts | Helm charts |
| **Container Registry** | None | Amazon ECR |
| **Database** | PostgreSQL on EC2 | RDS Aurora PostgreSQL (Multi-AZ) |
| **Cache** | None | ElastiCache Redis |
| **Secrets** | Plaintext `.env` on servers | HashiCorp Vault + AWS Secrets Manager |
| **Monitoring** | Basic CloudWatch alarms | Prometheus + Grafana + Loki (EKS) |
| **CDN** | None | CloudFront + S3 |
| **Security** | No WAF, open SGs | WAF on ALB, strict security groups via TF |
| **Networking** | Default VPC, manual SGs | Custom VPC, public/private subnets, NAT GW |
| **Deploy Frequency** | ~2x/week | Multiple times/day |
| **Mean Deploy Time** | ~2 hours | ~12 minutes |

## My Core Expertise Areas

### Infrastructure as Code
Terraform — modules, workspaces, remote state management with S3 + DynamoDB locking.
All AWS resources declared in code; zero manual console changes in production.

### Kubernetes / EKS
Migrated all services from bare EC2 to EKS. Wrote Helm charts for all apps.
Manages node groups, cluster autoscaler, RBAC, and namespace isolation.

### CI/CD
Designed GitHub Actions pipelines with reusable workflow templates shared across 12 repos.
Includes automated testing, security scanning, staging deploy, and prod gating.

### Observability
Deployed full Prometheus + Grafana + Loki stack on EKS using Helm.
Built dashboards for service SLOs, deploy frequency, and infrastructure health.

### Security
Vault integration for dynamic secrets. AWS IAM roles for service accounts (IRSA).
Shifted secrets management from plaintext files to zero-trust model.
