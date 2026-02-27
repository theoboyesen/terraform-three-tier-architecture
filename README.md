# Lab M4.09 - Recreate Project 1 with Terraform

## Architecture
- VPC with 6 subnets across 2 AZs
- ALB in public subnets
- 3 app servers in private subnets
- Security groups per tier

## Access
Application URL: http://project1-tf-alb-563351877.us-east-1.elb.amazonaws.com)

## Deployment
\`\`\`bash
terraform init && terraform apply
\`\`\`

## Comparison: Manual vs Terraform
- **Manual (Project 1):** ~2-3 hours
- **Terraform:** ~5 minutes
