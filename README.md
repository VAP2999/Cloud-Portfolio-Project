# **Master README for “Cloud Portfolio Project”**

```markdown
# Cloud Portfolio Project

**Student:** Vanshi Patel (002057295)  
**Course:** CSYE 6225 - Network Structures & Cloud Computing, Northeastern University  

This portfolio combines 3 major cloud projects demonstrating hands-on experience with **AWS, Terraform, FastAPI, Lambda, CI/CD, and serverless architecture**.

---

## Project Overview

This project consists of **three integrated components**:

1. **Web Application** – Full-stack REST API with FastAPI  
2. **Terraform AWS Infrastructure** – Automated cloud setup  
3. **Serverless Email Verification** – Lambda-based user email verification system  

Each component is in its own repository but linked here for a unified overview.

---

## Repositories

| Component | Repo Link | Description |
|-----------|-----------|-------------|
| Web Application | [Webapp_Cloud1](https://github.com/VAP2999/Webapp_Cloud1) | REST API for user and product management, image upload, deployed with Auto Scaling & ALB. |
| AWS Infrastructure | [Terraform_Cloud2](https://github.com/VAP2999/Terraform_Cloud2) | Terraform scripts to create VPC, EC2, RDS, DynamoDB, SNS, S3, IAM, and KMS. |
| Serverless Email Verification | [Serverless_Cloud3](https://github.com/VAP2999/Serverless_Cloud3) | Lambda function triggered via SNS to send user verification emails using SendGrid. |

---

## Architecture Overview

```

User → API → SNS → Lambda → DynamoDB
|
+→ RDS (PostgreSQL)
+→ S3 for storage
+→ ALB & Auto Scaling for compute

````

- **Webapp** handles user/product APIs
- **Serverless** ensures email verification
- **Terraform** automates infrastructure setup and security

---

## Key Features

- Full **CI/CD pipeline** for Webapp and Lambda functions
- Auto-scaling EC2 instances with health checks
- Encrypted storage using **KMS** and Secrets Manager
- FastAPI backend with SQLAlchemy & PostgreSQL
- SNS + Lambda serverless email verification
- GitHub Actions automated deployments
- Terraform-managed multi-account AWS infrastructure

---

## Local Development

### Webapp
```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload
pytest tests/ -v
````

### Serverless Lambda

```bash
pip install -r requirements.txt
# configure .env with environment variables (never commit secrets)
pytest tests/ -v
```

### Terraform

```bash
terraform init
terraform plan
terraform apply
```

---

## Deployment & CI/CD

* **Webapp:** Merges to `main` branch trigger GitHub Actions to build AMI, update ASG, and deploy to AWS.
* **Serverless:** Pushes trigger Lambda packaging and deployment to DEV & DEMO AWS accounts.
* **Terraform:** Validated on PRs, enforces `terraform fmt` and `terraform validate`.

---

## Security & Best Practices

* Secrets stored in **AWS Secrets Manager**
* KMS encryption for RDS, DynamoDB, S3, and Lambda
* HTTPS-only access in production
* Least-privilege IAM roles
* CI/CD ensures code quality and secure deployments

---

## How Email Verification Works

1. User registers → API publishes SNS event
2. Lambda triggered → checks DynamoDB for duplicates
3. Retrieves SendGrid key from Secrets Manager
4. Sends verification email with 1-minute token
5. Updates DynamoDB

---

## Tech Stack

* **Backend:** FastAPI, SQLAlchemy, Bcrypt
* **Database:** PostgreSQL, DynamoDB
* **Infrastructure:** Terraform, Packer, AWS (EC2, RDS, Lambda, S3, SNS, CloudWatch, ALB)
* **Serverless:** Lambda, SNS, DynamoDB
* **CI/CD:** GitHub Actions
* **Email Service:** SendGrid











