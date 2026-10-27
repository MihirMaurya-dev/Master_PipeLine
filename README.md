<div align="center">

# 🛡️ Enterprise Pre-Commit & DevSecOps Shift-Left Gate
### Automated Code Hygiene, Secret Scanning & Terraform Validation Hooks

[![Pre-Commit](https://img.shields.io/badge/Framework-Pre--Commit_v4.4-FAB040?style=for-the-badge&logo=pre-commit&logoColor=black)](https://pre-commit.com)
[![Secret Scanning](https://img.shields.io/badge/Security-Gitleaks_v8.18-00FF66?style=for-the-badge&logo=github&logoColor=0B0813)](https://github.com/gitleaks/gitleaks)
[![IaC Validation](https://img.shields.io/badge/IaC-Terraform_Lint_%26_Validate-7B2CBF?style=for-the-badge&logo=terraform&logoColor=white)](https://terraform.io)
[![Platform](https://img.shields.io/badge/Platform-Azure_DevOps_%26_GitHub-0078D7?style=for-the-badge&logo=azuredevops&logoColor=white)](https://dev.azure.com)

**Architected by [Mihir Maurya](https://github.com/MihirMaurya-dev) · Enterprise Cloud Architect & DevSecOps**  
[![Portfolio](https://img.shields.io/badge/Portfolio-mihirmaurya--dev.github.io-7B2CBF?style=flat-square&logo=googlechrome&logoColor=white)](https://mihirmaurya-dev.github.io/)
[![Live Project](https://img.shields.io/badge/Live_Project-b18g119.online-00FF66?style=flat-square&logo=cloudflare&logoColor=0B0813)](https://b18g119.online)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/mihirmauryaa1)

</div>

---

## 🏗️ Shift-Left Hook Architecture

This repository defines a centralized **Pre-Commit Enforcement Standard** for engineering teams. It blocks flawed syntax, unformatted Terraform blocks, and leaked credentials *before* commits ever reach the remote Git origin.

`mermaid
flowchart LR
    DEV[Developer Commit Attempt] --> PC[Git Pre-Commit Hook Engine]
    
    subgraph Hygiene["1. File & Format Hygiene"]
        PC --> W1[trailing-whitespace]
        PC --> W2[check-yaml & merge conflicts]
        PC --> W3[detect-private-key]
    end

    subgraph IaC["2. Terraform Static Verification"]
        PC --> T1[terraform_fmt]
        PC --> T2[terraform_validate]
        PC --> T3[terraform_tflint]
    end

    subgraph Secrets["3. Secret Scanning"]
        PC --> S1[Gitleaks Secret Detection]
    end

    Hygiene --> GATE{Passed?}
    IaC --> GATE
    Secrets --> GATE

    GATE -->|Yes| COMMIT[Git Commit Accepted 🟢]
    GATE -->|No| REJECT[Commit Blocked 🛑]

    classDef blueStyle fill:#08182b,stroke:#0078d7,stroke-width:2px,color:#fff;
    classDef greenStyle fill:#032111,stroke:#00ff66,stroke-width:2px,color:#fff;
    classDef redStyle fill:#2d0808,stroke:#ef4444,stroke-width:2px,color:#fff;

    class DEV,PC,W1,W2,W3,T1,T2,T3,S1 blueStyle;
    class COMMIT greenStyle;
    class REJECT redStyle;
`

---

## ⚡ Installation & Usage

`ash
# 1. Install pre-commit tool locally
pip install pre-commit

# 2. Install Git hooks into repository
pre-commit install

# 3. Manually run hooks across all files
pre-commit run --all-files
`

---

<div align="center">

**[Portfolio](https://mihirmaurya-dev.github.io/)** · **[LinkedIn](https://linkedin.com/in/mihirmauryaa1)** · **[DevOps Knowledge Vault](https://github.com/MihirMaurya-dev/DevOps-Notes)**

</div>