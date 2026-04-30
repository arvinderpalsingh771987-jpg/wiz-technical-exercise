# three-tier-security-demo

A deliberately vulnerable three-tier web application on AWS, built to demonstrate 
common cloud security misconfigurations, attack paths, and detection controls.

## Architecture

- **Web Tier** — Containerised Go application (Tasky) deployed on EKS (Kubernetes)
- **Database Tier** — MongoDB on EC2 (intentionally misconfigured)
- **Storage Tier** — S3 bucket for database backups (intentionally misconfigured)

## Intentional Misconfigurations

This environment contains deliberate security weaknesses for educational purposes:

- SSH open to 0.0.0.0/0 on the database server
- Outdated OS and database software with known CVEs
- Overpermissive IAM role on EC2 (AdministratorAccess)
- Database in a public subnet
- S3 bucket with Block Public Access disabled
- Kubernetes workload running with cluster-admin privileges
- EKS worker nodes in public subnets

## DevOps

- Infrastructure as Code using AWS CloudFormation
- Two CI/CD pipelines via GitHub Actions
- OIDC federation for secure AWS authentication — no static credentials stored

## Security Controls

- AWS CloudTrail for control plane audit logging
- AWS Config with targeted compliance rules
- AWS GuardDuty for runtime threat detection
- AWS Security Hub for unified findings view

## Warning

> This environment contains **intentional security misconfigurations** for 
> educational purposes. Do not deploy in a production AWS account.

## Prerequisites

- AWS Account
- Docker Desktop
- AWS CLI configured
- kubectl installed
- GitHub account with Actions enabled
