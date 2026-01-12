# AU/NZ Cloud Portfolio — review path + demos

This repo is the quickest way to review my work for Cloud / DevOps / Infrastructure roles (AU/NZ focus). It links to 6 projects in the order I'd walk through them in an interview — each one builds on the last.

## If you only have 5 minutes

1) **AWS Terraform baseline** (infra demo: create → verify → destroy)
   Repo: https://github.com/justin-henson/au-nz-cloud-baseline-aws
   What to look for: VPC layout, ALB → target group → private EC2 via SSM, cost controls.

2) **CI/CD pipeline** (automated deployment with safety gates)
   Repo: https://github.com/justin-henson/au-nz-cicd-pipeline
   What to look for: GitHub Actions workflows, Terraform plan/apply gates, drift detection.

3) **Kubernetes baseline** (EKS with security hardening)
   Repo: https://github.com/justin-henson/au-nz-k8s-baseline-eks
   What to look for: Pod Security Standards, IRSA, network policies, resource limits.

4) **Observability stack** (monitoring + alerting + SLOs)
   Repo: https://github.com/justin-henson/au-nz-observability-stack
   What to look for: CloudWatch alarms, Prometheus alert rules, SLO definitions, error budgets.

5) **Ops / SRE runbooks** (operate + recover + improve)
   Repo: https://github.com/justin-henson/au-nz-ops-runbooks
   What to look for: incident response, postmortems, change/DR checklists.

## How it all connects

```
Build (Terraform) → Deploy (CI/CD) → Run (EKS) → Monitor (Observability) → Respond (Runbooks)
     [1]               [2]            [3]              [4]                      [5]
```

These aren't isolated demos — the CI/CD pipeline deploys the Terraform that provisions the EKS cluster. The observability stack monitors that cluster. When alerts fire, the runbooks tell you what to do.

## What I can explain live (interview walkthrough)

**Infrastructure:**
- Why private subnets + SSM (no inbound SSH) is safer and simpler to operate
- ALB routing, target health checks, and why the app listens on port 8080
- Why VPC interface endpoints remove the need for NAT for SSM traffic

**CI/CD:**
- How drift detection catches manual changes before they cause incidents
- Why plan output is posted to PRs for human review before apply
- How the pipeline handles Terraform state locking and failure recovery

**Kubernetes:**
- IRSA vs node-level IAM roles — why per-pod identity is the security standard
- How Pod Security Standards enforce restricted mode and block privilege escalation
- Network policies for default-deny with explicit allow rules

**Monitoring & SRE:**
- SLO-based decision making — error budgets determine when to freeze deployments
- Alert routing design — severity drives notification channel and response time
- Why dual-stack monitoring (CloudWatch + Prometheus) covers both AWS services and workloads

**Operations:**
- How I keep demo infrastructure repeatable and easy to tear down
- How I'd evolve this for production (HTTPS, ASG, remote state, OIDC auth)

## Portfolio map

| Repo | What it demonstrates | Proof / how to verify |
|------|----------------------|------------------------|
| [`au-nz-cloud-baseline-aws`](https://github.com/justin-henson/au-nz-cloud-baseline-aws) | Terraform AWS baseline, private EC2 via SSM, ALB ingress | Run the **Proof** steps in the README |
| [`au-nz-cicd-pipeline`](https://github.com/justin-henson/au-nz-cicd-pipeline) | GitHub Actions CI/CD with drift detection | Check the GitHub Actions tab for passing workflows |
| [`au-nz-k8s-baseline-eks`](https://github.com/justin-henson/au-nz-k8s-baseline-eks) | EKS with security hardening, IRSA, Pod Security Standards | Review `k8s/` manifests and Terraform config |
| [`au-nz-observability-stack`](https://github.com/justin-henson/au-nz-observability-stack) | CloudWatch + Prometheus monitoring, SLOs, alert-driven runbooks | Check `terraform/`, `prometheus/`, `slo/` directories |
| [`au-nz-ops-runbooks`](https://github.com/justin-henson/au-nz-ops-runbooks) | Ops maturity: incident/change/DR templates | Open incident response and postmortem templates |

## Role fit (AU/NZ)

- Target roles: Cloud / DevOps / Infrastructure / SRE
- Based in Texas (CT) — can overlap 12:00pm–4:00pm NZT or 8:00am–2:00pm AEDT
- Open to sponsorship and relocation

## Contact

- LinkedIn: https://www.linkedin.com/in/justin-henson/
- Email: justin.henson@pm.me

*Built with ☕ for AU/NZ DevOps opportunities*
