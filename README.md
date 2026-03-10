# Recreating a 3-Tier Architecture with Terraform

This project recreates the **3-tier architecture from Project 1**, but instead of building it manually through the AWS console, the entire infrastructure is provisioned using **Terraform**.

The goal of this exercise was to demonstrate how **Infrastructure as Code (IaC)** can reproduce the same environment automatically and consistently.

In the original project, the architecture was built step-by-step through the AWS console. In this version, the **entire stack is defined in Terraform configuration files and deployed with a single command**.

---

# Project Context

In **Project 1**, the infrastructure was created manually using the AWS console:

- Creating a VPC  
- Configuring subnets  
- Attaching route tables  
- Creating security groups  
- Deploying EC2 instances  
- Configuring an Application Load Balancer  
- Registering instances with a target group  

While this approach is useful for learning AWS concepts, it is **time-consuming and difficult to reproduce consistently**.

This project demonstrates how the same architecture can be recreated using **Infrastructure as Code**, allowing the entire environment to be deployed automatically.

---

# What Terraform Changes

Instead of manually configuring infrastructure resources, Terraform allows the entire system to be defined in code.

### Manual approach

```
Click through AWS console → configure resources → repeat steps manually
```

### Terraform approach

```
Define infrastructure in code → terraform apply → infrastructure deployed automatically
```

Benefits of using Terraform include:

- **Repeatable deployments**
- **Version-controlled infrastructure**
- **Faster provisioning**
- **Reduced manual configuration errors**

---

# Infrastructure Deployed

This Terraform configuration recreates the same architecture as the manual project:

- VPC spanning **two availability zones**
- **6 subnets** (public, application, and data tiers)
- **Internet Gateway and NAT Gateway**
- **Application Load Balancer**
- **Target group with health checks**
- **Multiple EC2 application servers**
- **Security groups enforcing tier isolation**

The application instances are placed behind an **Application Load Balancer**, which distributes traffic across instances.

---

# Project Structure

The Terraform configuration is separated into multiple files to keep the infrastructure organised.

```
.
├── main.tf
├── variables.tf
├── outputs.tf
├── networking.tf
├── security-groups.tf
├── alb.tf
├── compute.tf
└── README.md
```

| File | Purpose |
|-----|-----|
| `variables.tf` | Defines configurable infrastructure parameters |
| `networking.tf` | Creates VPC, subnets, gateways, and route tables |
| `security-groups.tf` | Defines security groups controlling traffic |
| `alb.tf` | Configures the Application Load Balancer |
| `compute.tf` | Deploys EC2 instances and registers them with the load balancer |
| `outputs.tf` | Provides useful deployment outputs |

---

# Deployment Steps

### 1. Initialise Terraform

```bash
terraform init
```

This downloads the required Terraform providers and prepares the working directory.

---

### 2. Format and validate the configuration

```bash
terraform fmt
terraform validate
```

These commands ensure the Terraform code is properly formatted and syntactically correct.

---

### 3. Preview infrastructure changes

```bash
terraform plan
```

Terraform generates an execution plan showing which resources will be created.

---

### 4. Deploy the infrastructure

```bash
terraform apply
```

Terraform provisions the entire environment defined in the configuration files.

---

# Testing the Deployment

Once Terraform finishes provisioning, the **Application Load Balancer DNS name** can be retrieved:

```bash
terraform output alb_url
```

Opening this URL should return the web application served by the EC2 instances behind the load balancer.

Refreshing the page multiple times should show **different instance IDs**, demonstrating load balancing across the application tier.

---

# Key Takeaways

Rebuilding the project with Terraform highlighted several important concepts:

- Infrastructure can be **fully automated using code**
- Complex environments can be **recreated quickly and consistently**
- Terraform makes infrastructure **repeatable and version controlled**
- Infrastructure definitions can be stored and maintained in **Git repositories**

Compared to the manual console deployment, Terraform significantly improves **speed, reproducibility, and maintainability** of cloud infrastructure.

---

# Related Project

This project is a Terraform-based recreation of the original manual deployment:

- **Manual AWS Console Deployment:** github.com/theoboyesen/three-tier-cloud-arhcitecture-deployment
- **Terraform Infrastructure as Code Version:** github.com/theoboyesen/terraform-three-tier-architecture

Both projects demonstrate the same architecture implemented using two different approaches.
