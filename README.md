# 🚀 Terraform Infra Pipeline com GitHub Actions e AWS

Pipeline completa de **Infraestrutura como Código (IaC)** utilizando **Terraform**, **GitHub Actions** e **AWS**, com autenticação segura via **OIDC**, backend remoto em **S3 + DynamoDB**, suporte a **múltiplos ambientes (DEV e PROD)** e execução automatizada de **plan, apply e destroy**.

---

## 📌 Visão Geral

Este projeto demonstra como construir uma **pipeline profissional de infraestrutura**, eliminando o uso de credenciais estáticas na AWS e garantindo:

- Segurança
- Escalabilidade
- Reprodutibilidade
- Separação de ambientes
- Automação completa via CI/CD

O fluxo foi pensado para simular um **cenário real de produção**, semelhante ao utilizado por times de Cloud e DevOps.

---

## 🏗️ Arquitetura

- **Terraform**
  - Provisionamento de recursos AWS
  - Gerenciamento de estado remoto
  - Workspaces por ambiente
- **GitHub Actions**
  - CI/CD para infraestrutura
  - Workflows reutilizáveis
- **AWS**
  - S3 (Statefile)
  - DynamoDB (Lock)
  - IAM + OIDC (autenticação segura)

---

## 🔐 Segurança (OIDC)

A autenticação entre GitHub Actions e AWS é feita via **OpenID Connect (OIDC)**, evitando:

❌ Access Key  
❌ Secret Key  
❌ Credenciais expostas  

✔️ Autenticação temporária  
✔️ Menor superfície de ataque  
✔️ Boas práticas de segurança em Cloud

---

## 📁 Estrutura do Projeto

```bash
terraform-infra-pipeline/
│
├── .github/
│   └── workflows/
│       ├── terraform.yml      # Workflow reutilizável (Terraform)
│       ├── develop.yml        # Deploy DEV
│       └── main.yml           # Deploy PROD
│
├── infra/
│   ├── envs/
│   │   ├── dev/
│   │   │   └── terraform.tfvars
│   │   └── prod/
│   │       └── terraform.tfvars
│   │
│   ├── main.tf
│   ├── backend.tf
│   ├── provider.tf
│   ├── variables.tf
│   └── destroy_config.json
│
├── .gitignore
└── README.md
