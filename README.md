# 🚀 Node.js CI/CD Pipeline on AWS (Terraform + GitHub Actions + ECS Fargate)

This project demonstrates a **full CI/CD pipeline** for deploying a Node.js web application to AWS ECS Fargate using Terraform and GitHub Actions.

---

## 🧱 Project Overview

### 🔹 Stack Used
- **Terraform** — Infrastructure as Code  
- **AWS ECS Fargate** — Container orchestration  
- **AWS ECR** — Container image registry  
- **AWS ALB** — Application Load Balancer  
- **GitHub Actions** — CI/CD automation  
- **Docker** — Containerization  
- **Node.js / Express** — Web application  

---

## ⚙️ Architecture

[GitHub Actions]
↓
[Docker build + push]
↓
[AWS ECR] ← stores image
↓
[AWS ECS Fargate] ← runs container
↓
[AWS ALB] ← public access


---

## 🧩 Terraform Modules

| Component | Description |
|------------|--------------|
| `vpc` | Network (VPC, subnets, route tables, IGW) |
| `security_groups` | Access rules for ALB and ECS |
| `ecr` | Private Docker image registry |
| `ecs` | Cluster, service, and task definition |
| `alb` | Load balancer with listener and target group |

---

## 🔄 CI/CD Workflow

### 1. **GitHub Actions Workflow**
File: `.github/workflows/deploy.yml`

Pipeline steps:
1. Checkout source code  
2. Configure AWS credentials  
3. Build and push Docker image to ECR  
4. Force ECS service to deploy new version  

### 2. **Terraform Deployment**
```bash
cd terraform
terraform init
terraform apply -auto-approve
🌍 Access the Application
After successful deployment, Terraform outputs:

alb_dns_name = "webapp-alb-XXXX.us-east-1.elb.amazonaws.com"
Open in your browser:


http://webapp-alb-XXXX.us-east-1.elb.amazonaws.com
🧠 What I Learned
End-to-end DevOps flow (IaC → CI/CD → Cloud deployment)

AWS ECS + ECR + ALB integration

GitHub Actions pipelines for container delivery

Working with Terraform modules and states

Debugging IAM, ECS, and networking issues

🗑️ Cleanup
To remove all AWS resources:

cd terraform
terraform destroy 
