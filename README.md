# Lab M4.09 - Recreate Project 1 with Terraform

**Course:** Cloud Engineering Bootcamp - Week 4
**Estimated Time:** 120-180 minutes (Major Lab)

## 🎯 Objectives

- Recreate complete Project 1 using Terraform
- Build 3-tier architecture as code
- Deploy Application Load Balancer
- Compare manual vs IaC approach

## 📁 Repository Structure

```
ce-lab-project1-terraform/
├── README.md
├── ARCHITECTURE.md
├── COMPARISON.md
├── main.tf
├── modules/
│   ├── vpc/
│   ├── alb/
│   ├── compute/
│   └── security-groups/
├── variables.tf
├── outputs.tf
├── architecture-diagram.png
└── screenshots/
```

## ✅ Grading (100pts)

- Network infrastructure: 20pts
- Security groups: 15pts
- ALB configuration: 20pts
- Compute tier: 20pts
- Database tier: 10pts
- Comparison analysis: 10pts
- Documentation: 5pts

## 🌟 Bonus (20pts)

- Auto Scaling Group: 10pts
- RDS deployment: 5pts
- CloudWatch dashboards: 5pts
