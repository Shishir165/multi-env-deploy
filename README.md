# 🚀 Multi-Environment CI/CD Deployment with GitHub Actions

This project demonstrates a **real-world CI/CD pipeline** using **GitHub Actions** to deploy a static website across **multiple environments** (`development`, `staging`, `production`) using **branch-based promotion** and **Pull Requests**.

---

## 📌 Project Overview

The objective of this lab was to:

- Build a CI/CD pipeline using GitHub Actions
- Use GitHub Environments with environment-specific variables and secrets
- Deploy a website to an AWS EC2 instance
- Promote code through environments using Pull Requests
- Simulate a real-world Dev → Staging → Production workflow

---

## 🧱 Architecture

dev branch → development environment
staging branch → staging environment
main branch → production environment


Each environment has:
- A separate deployment path
- Unique UI color and title
- Environment-scoped variables and secrets

---

## 🌿 Branch & Environment Mapping

| Branch   | Environment   | URL |
|--------|---------------|-----|
| dev | development | http://dev.<EC2_PUBLIC_IP>.nip.io |
| staging | staging | http://staging.<EC2_PUBLIC_IP>.nip.io |
| main | production | http://<EC2_PUBLIC_IP>.nip.io |

---

## ⚙️ Technologies Used

- GitHub Actions – CI/CD automation  
- GitHub Environments – environment isolation  
- AWS EC2 (Ubuntu) – application hosting  
- Nginx – web server  
- SSH – secure deployment  
- HTML, CSS, JavaScript – frontend  

---

## 🧪 CI/CD Workflow

The GitHub Actions workflow performs the following steps:

1. Triggers on push to `dev`, `staging`, or `main`
2. Maps the branch to the correct environment
3. Replaces placeholders in files:
   - `__SITE_TITLE__`
   - `__SITE_COLOR__`
   - `__DEPLOY_TIME__`
   - `__COMMIT_SHA__`
4. Deploys files to EC2 using SSH
5. Verifies deployment on the server

Workflow file location:
.github/workflows/deploy.yml


---

## 🔐 Environment Configuration

Each GitHub Environment contains:

### Secrets
- `SSH_PRIVATE_KEY` – SSH private key for EC2 access

### Variables
- `DEPLOY_HOST`
- `DEPLOY_PATH`
- `DEPLOY_USER`
- `SITE_TITLE`
- `SITE_COLOR`

This allows environment-specific behavior without modifying application code.

---

## 🔄 Promotion Flow (Pull Request Based)

Code promotion follows a real-world workflow:

### Dev → Staging
- Pull Request created from `dev` to `staging`
- Merge triggers deployment to the staging environment

### Staging → Production
- Pull Request created from `staging` to `main`
- Merge triggers deployment to production

---

## 🌐 Live Deployment Verification

Each deployed environment displays:
- Environment name
- Unique color
- Deployment timestamp
- Commit SHA

This makes it easy to verify **what version is deployed and where**.

---

## ✅ Final Outcome

- Fully automated CI/CD pipeline
- Secure SSH-based deployment
- Environment-specific configuration
- PR-driven promotion workflow
- Production-style DevOps setup

---

## 🧠 Key Learnings

- Designing multi-environment CI/CD pipelines
- Using GitHub Actions and Environments effectively
- Secure SSH automation
- Debugging CI/CD and deployment issues
- Applying real-world DevOps best practices

---

## 📎 Conclusion

This lab successfully demonstrates how modern teams deploy applications using GitHub Actions, environment isolation, and Pull Request–based promotion, closely mirroring real-world production workflows.

