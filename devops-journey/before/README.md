# Before: State of Infrastructure When I Joined (Jan 2023)

This section captures the environment I inherited when I joined NovaTech Solutions.
Used as the 'starting point' in interview narratives.

## Summary

When I joined, the infrastructure was a mix of manually managed EC2 instances,
a fragile Jenkins setup, and no standardized deployment process.
Deployments were feared events — often done manually at night.

## Key Pain Points

- No Infrastructure as Code (all resources created by hand in AWS Console)
- Jenkins CI server was a single point of failure, running on one EC2 instance
- No container orchestration — apps ran directly on EC2 with `systemd`
- Secrets stored in plaintext in config files on servers
- Staging and production environments were snowflakes — never truly identical
- Mean time to deploy: ~2 hours; rollback was manual and risky

## Diagrams & Details

- See `architecture-diagram.md` for a description of the legacy architecture
