<div align="center">

# 🤖 Enterprise Multi-Directory Terraform CI/CD Bot & Pre-Commit Security Engine
### Dynamic Matrix Change Detection, Autonomous Pull Request Telemetry, Infracost FinOps & Client-Side Git Hooks

[![CI/CD Bot Status](https://github.com/MihirMaurya-dev/Master_PipeLine/actions/workflows/terraform.yml/badge.svg)](https://github.com/MihirMaurya-dev/Master_PipeLine/actions/workflows/terraform.yml)
[![Platform](https://img.shields.io/badge/Platform-Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://azure.microsoft.com)
[![IaC Engine](https://img.shields.io/badge/IaC-HashiCorp_Terraform_v1.9+-7B2CBF?style=for-the-badge&logo=terraform&logoColor=white)](https://terraform.io)
[![CI/CD Bot](https://img.shields.io/badge/CI%2FCD-Dynamic_Matrix_Bot-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![FinOps](https://img.shields.io/badge/FinOps-Infracost_PR_Deltas-00E5FF?style=for-the-badge&logo=infracost&logoColor=0B0813)](https://www.infracost.io/)
[![Pre-Commit](https://img.shields.io/badge/Hooks-Pre--Commit_v4.4+-FAB040?style=for-the-badge&logo=precommit&logoColor=0B0813)](https://pre-commit.com/)

**Architected by [Mihir Maurya](https://github.com/MihirMaurya-dev) · Cloud Solutions Architect & DevSecOps Engineer**  
[![Portfolio](https://img.shields.io/badge/Portfolio-mihirmaurya--dev.github.io-7B2CBF?style=flat-square&logo=googlechrome&logoColor=white)](https://mihirmaurya-dev.github.io/)
[![Live Platform](https://img.shields.io/badge/Live_Project-b18g119.online-00FF66?style=flat-square&logo=cloudflare&logoColor=0B0813)](https://b18g119.online)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/mihirmauryaa1)

</div>

---

## 🧭 Executive Overview

**`Master_PipeLine`** is an advanced DevSecOps automation suite engineered for monorepos and multi-directory Terraform platforms. It merges **client-side git pre-commit hooks** with an autonomous **GitHub Actions CI/CD bot** that dynamically detects file-level modifications, spins up isolated parallel matrix jobs per infrastructure directory, scans for leaked secrets, audits IaC vulnerabilities, and writes execution plans and **Infracost financial breakdowns** directly onto GitHub Pull Requests.

```mermaid
flowchart TD
    subgraph Client["💻 Local Workstation (Shift-Left Pre-Commit)"]
        A[Git Commit Trigger] --> B[Pre-Commit Framework]
        B --> C[trailing-whitespace & eof-fixer]
        B --> D[detect-private-key & gitleaks]
        B --> E[terraform_fmt & terraform_validate]
        E --> F[Commit Permitted & Pushed 🟢]
    end

    subgraph CI["⚡ Cloud CI/CD Matrix Bot (GitHub Actions)"]
        F --> G[Global Security Scans]
        G --> H[Gitleaks Secret Audit]
        G --> I[TruffleHog Verified Scans]
        G --> J[Trivy IaC Configuration Audit]

        F --> K[Dynamic Matrix Path Detection\ntj-actions/changed-files]
        K --> L{Any .tf Directories Modified?}
        L -- No --> M[Skip Matrix Jobs & Complete CI]
        L -- Yes --> N[Spawn Dynamic Parallel Runners\nubuntu-latest]
    end

    subgraph Matrix["📐 Parallel Terraform Execution Matrix"]
        N --> O[terraform fmt -check]
        O --> P[terraform init -backend=false]
        P --> Q[terraform validate & TFLint]
        Q --> R[Speculative terraform plan]
        R --> S[Infracost Budget Breakdown]
    end

    subgraph Bot["💬 Automated Pull Request Feedback Engine"]
        R --> T[actions/github-script: Inject Plan Comment on PR]
        S --> U[infracost comment: Post Financial Diff on PR]
    end

    classDef darkPurple fill:#140728,stroke:#7B2CBF,stroke-width:2px,color:#fff;
    classDef cyberGreen fill:#032111,stroke:#00FF66,stroke-width:2px,color:#fff;
    classDef azureBlue fill:#08182b,stroke:#0078D4,stroke-width:2px,color:#fff;
    classDef goldenYellow fill:#2b2005,stroke:#FAB040,stroke-width:2px,color:#fff;

    class A,B,C,D,E,F goldenYellow;
    class G,H,I,J cyberGreen;
    class K,L,M,N,O,P,Q,R,S azureBlue;
    class T,U darkPurple;
```

---

## 🧰 Technology Stack & Tooling

<div align="center">

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=azure,terraform,githubactions,git,linux,bash,powershell,vscode&perline=8" alt="Technology Stack" />
</a>

</div>

<br/>

| Domain | Tools & Frameworks | Description & Engineering Role |
|---|---|---|
| ☁️ **Cloud Platform** | Microsoft Azure (`azurerm` v4.73+) | Resource Groups, Virtual Networks, Dynamic Subnets |
| 🏗️ **Infrastructure as Code** | HashiCorp Terraform v1.9+, HCL | Modular directory architecture (`new/modules/infrastructure`) |
| 🤖 **Automation Bot** | GitHub Actions & `actions/github-script@v7` | Dynamic matrix path detection & automated PR telemetry commenting |
| 💰 **FinOps & Cost Governance** | Infracost CLI & GitHub Actions Action | Automated monthly cost breakdown & PR financial delta posting |
| 🔐 **DevSecOps & Supply Chain** | Gitleaks, TruffleHog, Trivy, TFLint | High-entropy secret detection, verified token scanning & SAST |
| 🛡️ **Client-Side Shift-Left** | Pre-Commit Framework v4.4+ | Pre-commit git hooks preventing bad commits from reaching remotes |

---

## 📂 Repository Topology

```plaintext
Master_PipeLine/
├── .github/
│   └── workflows/
│       └── terraform.yml           # 🤖 Autonomous Multi-Directory Matrix Bot
├── .vscode/
│   ├── extensions.json             # Recommended developer IDE extensions
│   └── settings.json               # VSCode linting, formatting & Terraform configs
├── new/                            # 📦 Target Infrastructure Module
│   ├── modules/
│   │   └── infrastructure/         # 🏛️ Core Cloud Blueprint Module
│   │       ├── main.tf             # Azure RG, VNet & Subnet definitions
│   │       ├── outputs.tf          # Exported resource identifiers
│   │       └── variables.tf        # CIDR blocks & regional parameters
│   ├── main.tf                     # Root caller invoking ./modules/infrastructure
│   └── variable.tf                 # Base naming & region validation constraints
├── .gitignore                      # Terraform caches, plan files & secret exclusions
├── .pre-commit-config.yaml         # 🛡️ Declarative Client-Side Git Hooks Specification
└── README.md                       # Enterprise Architectural Documentation
```

---

## 🛡️ Pre-Commit Shift-Left Security Specifications

The client-side gating framework is defined in [`.pre-commit-config.yaml`](./.pre-commit-config.yaml) and executes locally on every `git commit`:

```yaml
repos:
  # 1. Cleanliness & Integrity
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-merge-conflict
      - id: detect-private-key

  # 2. Terraform Static Verification
  - repo: https://github.com/antonbabenko/pre-commit-terraform
    rev: v1.81.0
    hooks:
      - id: terraform_fmt
      - id: terraform_validate
      - id: terraform_tflint

  # 3. Secret Leak Prevention
  - repo: https://github.com/gitleaks/gitleaks
    rev: v8.18.0
    hooks:
      - id: gitleaks
```

---

## 🤖 The CI/CD Matrix Bot Workflow Lifecycle

### Stage 1: Global Security & Secret Scanners
Executes across the full repository on push/PR:
- **Gitleaks**: Scans commit history for API tokens, certificates, and private credentials.
- **TruffleHog**: Audits high-entropy strings and verifies live validity against known provider endpoints.
- **Trivy**: Evaluates Terraform configuration against CIS Microsoft Azure Security benchmarks.

### Stage 2: Dynamic Matrix Path Detection
Rather than running full pipelines blindly across unchanged directories, the bot leverages `tj-actions/changed-files@v44` to identify only directories containing `.tf` file modifications. It emits a dynamic JSON array:
```json
["new", "environments/prod"]
```

### Stage 3: Dynamic Parallel Runners & PR Feedback
For each directory in the matrix:
1. Initializes Terraform with `-backend=false` for stateless validation.
2. Checks syntax formatting and deep schema correctness (`terraform validate`).
3. Executes **TFLint** with modular rulesets.
4. Generates an execution plan and **posts the formatted plan diff directly into the PR comments**.
5. Runs **Infracost** to estimate cloud costs and injects an interactive table showing monthly operational cost deltas.

---

## ⚡ Local Setup & Hook Installation

### 1. Install Pre-Commit Framework
```bash
# Using pip
pip install pre-commit

# Or using Homebrew / Chocolatey
choco install pre-commit
```

### 2. Install Git Hooks
```bash
cd Master_PipeLine
pre-commit install
```

### 3. Run Pre-Commit Across All Files
```bash
pre-commit run --all-files
```

### 4. Test Infrastructure Locally
```bash
cd new
terraform init -backend=false
terraform fmt -check
terraform validate
```

---

## 👨‍💻 Author & Engineering Profile

**Mihir Maurya**  
*Cloud Solutions Architect & DevSecOps Engineer*  
*M.Sc Computer Science & Computer Applications & Mathematics Graduate*

* 🌐 **Portfolio**: [mihirmaurya-dev.github.io](https://mihirmaurya-dev.github.io/)
* 🚀 **Live Production Platform**: [b18g119.online](https://b18g119.online)
* 💼 **LinkedIn**: [linkedin.com/in/mihirmauryaa1](https://linkedin.com/in/mihirmauryaa1)
* 🐙 **GitHub**: [@MihirMaurya-dev](https://github.com/MihirMaurya-dev)

---

<div align="center">

**[Overview](#-executive-overview)** · **[Architecture Diagram](#-executive-overview)** · **[Tech Stack](#-technology-stack--tooling)** · **[Pre-Commit Spec](#-pre-commit-shift-left-security-specifications)** · **[Bot Workflow](#-the-cicd-matrix-bot-workflow-lifecycle)**

*Engineered with precision for zero-trust cloud infrastructure and automated GitOps feedback.*

</div>
