# Current Architecture (Built 2023–2024)

> Diagram description — visual diagrams (PNG/SVG) will be added to this folder.

## High-Level Overview

```
                  ┌─────────────────────────────────────────────────────┐
                  │                    AWS us-east-1                    │
                  │                                                     │
  Internet ──────►│  ALB (Terraform-managed, WAF enabled)              │
                  │    │                                                 │
                  │    └──► EKS Cluster (3 node groups)                │
                  │           ├── Namespace: payflow (prod)             │
                  │           ├── Namespace: payflow (staging)          │
                  │           └── Namespace: platform-tools             │
                  │                                                     │
                  │  RDS Aurora PostgreSQL (Multi-AZ)                  │
                  │  ElastiCache Redis (session & cache)                │
                  │  S3 + CloudFront (static assets & CDN)             │
                  │  Secrets Manager + HashiCorp Vault                  │
                  │  ECR (private container registry)                   │
                  └─────────────────────────────────────────────────────┘
```

## Tech Stack (Current)

- **Cloud:** AWS — managed entirely with Terraform (remote state in S3 + DynamoDB lock)
- **Containers:** Docker + Amazon EKS (Kubernetes 1.29)
- **CI/CD:** GitHub Actions with reusable workflows
- **IaC:** Terraform modules, organized per environment
- **Secrets:** HashiCorp Vault + AWS Secrets Manager
- **Monitoring:** Prometheus + Grafana + Loki (deployed via Helm on EKS)
- **Registry:** Amazon ECR
- **Networking:** VPC with public/private subnets, NAT Gateway, VPC endpoints
