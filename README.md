<div align="center">

# 🏗️ Infrastructure Pipeline ✨

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&pause=1000&color=2196F3&center=true&vCenter=true&width=435&lines=Infrastructure+As+Code;Terraform+%2B+GitHub+Actions;Automate.+Secure.+Deploy.)](https://git.io/typing-svg)

This repository contains a robust, automated **CI/CD pipeline** for provisioning Infrastructure as Code (IaC) using Terraform and GitHub Actions. The pipeline is designed to ensure code quality, security, and cost visibility before any infrastructure changes are applied to Azure. ☁️

</div>

---

## 🚀 Pipeline Overview

The pipeline runs automatically on:
- 📌 `push` to any branch
- 🔀 `pull_request` targeting the `main` branch

It consists of four distinct, powerful stages:

### 🕵️ Stage 0: Secrets Scanning
- Uses **Gitleaks** 💧 to scan the repository for any hardcoded secrets or credentials to prevent accidental exposure of sensitive data.

### 🧹 Stage 1: Code Review (Fmt, Lint, Validate)
- 📝 **Terraform Format:** Checks if the Terraform code is formatted correctly (`terraform fmt`).
- ✅ **Terraform Validate:** Validates the syntax and configuration of the Terraform files (`terraform validate`).
- 🔍 **TFLint:** Runs a deep static analysis of the Terraform code to enforce best practices and catch potential errors.

### 🛡️ Stage 2: IaC Security Scan
- Uses **Checkov** 🦉 to scan the Terraform code for security misconfigurations and compliance violations.
- 📈 Uploads the results as a SARIF file directly to the GitHub Security tab for easy visibility and tracking.

### 💰 Stage 3: Terraform Plan
- 🔐 **Azure Authentication:** Authenticates to Azure securely using OpenID Connect (OIDC).
- 🏗️ **Terraform Plan:** Generates an execution plan showing what changes will be applied (`terraform plan`).
- 💵 **Cost Estimation:** Uses **Infracost** to calculate the cloud cost implications of the PR and automatically posts a cost breakdown as a comment on the Pull Request.
- 📩 **Artifacts & Notifications:** Saves the plan output as a downloadable GitHub artifact and automatically emails the full plan output to the designated stakeholders.

---

## 🔐 Required Secrets

To successfully run this pipeline, the following secrets must be configured in your GitHub repository settings:

| Secret Name | Description |
|---|---|
| 🔑 `AZURE_CLIENT_ID` | Client ID of the Azure Service Principal used for OIDC authentication. |
| 🔑 `AZURE_TENANT_ID` | Tenant ID of your Azure Active Directory. |
| 🔑 `AZURE_SUBSCRIPTION_ID` | The Azure Subscription ID where resources will be deployed. |
| 💸 `INFRACOST_API_KEY` | API key for Infracost to generate cost breakdowns. |
| 📧 `MAIL_USERNAME` | The sender's email address (for emailing the plan). |
| 🔓 `MAIL_PASSWORD` | The SMTP password or app password for the sender's email. |
| 🎯 `MAIL_TO` | The recipient email address for the Terraform plan. |

---

## 📁 Directory Structure

```text
📦 Infrastructure-pipeline
 ┣ 📂 .github/workflows
 ┃ ┗ 📜 pipeline.yml        # The main GitHub Actions workflow file ⚙️
 ┣ 📂 Environment
 ┃ ┗ 📂 Dev                 # The working directory for Dev environment 🌍
 ┗ 📜 README.md
```

---

## 🛠 Tools & Tech Stack

<p align="center">
  <img src="https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white" />
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white" />
  <img src="https://img.shields.io/badge/Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white" />
  <img src="https://img.shields.io/badge/Checkov-1E1E1E?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Infracost-000000?style=for-the-badge" />
</p>
