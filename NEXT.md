# What I’d improve next (roadmap)

- HTTPS with ACM + 443 listener, redirect 80 → 443
- Replace single EC2 with an Auto Scaling Group behind the target group
- CloudWatch alarms + dashboards (ALB 5XX, target health, instance CPU/mem)
- ALB access logs to S3 + app logs to CloudWatch
- Remote state + locking (S3 + DynamoDB) for team workflows
- CI checks: terraform fmt/validate, tflint, security scanning (checkov)
