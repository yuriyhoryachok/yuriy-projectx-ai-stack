# Interview Stories (STAR Format)

Key talking points for behavioral and technical interviews, structured as STAR stories.

---

## Story 1: Rescuing a Broken Deployment Pipeline

**Situation:** When I joined NovaTech, Jenkins was a single EC2 instance with no backups.
It had crashed twice in the prior 6 months, halting all releases.

**Task:** Modernize CI/CD without disrupting ongoing feature development.

**Action:** I designed a parallel GitHub Actions setup, migrated services one by one over
3 months, and built reusable workflow templates the whole engineering org could adopt.

**Result:** Deploy frequency increased from ~2x/week to multiple times per day.
Mean deploy time dropped from ~2 hours to 12 minutes. Zero pipeline outages in 18 months.

---

## Story 2: Kubernetes Migration

**Situation:** All apps ran on bare EC2 with `systemd`. Scaling required manual intervention
and environments drifted from each other over time.

**Task:** Migrate to containers and Kubernetes to improve scalability and consistency.

**Action:** Led a 4-month EKS migration. Built Docker images for each service, wrote Helm
charts, and set up staging/prod namespaces with identical configurations.

**Result:** Auto-scaling now handles 3x traffic spikes without manual work.
Staging and production are now truly identical environments.

---

> More stories will be added as projects evolve.
