# 🔐 Zero Trust Homelab — Proxmox & Netbird Architecture

> A self-hosted, production-grade hybrid lab environment running 24/7 
> with real workloads and Zero Trust Network Access.

---

## 📋 Overview

This homelab was independently designed and deployed to build 
real-world skills in cybersecurity, infrastructure management, 
and cloud integration — going well beyond typical lab environments.

**Key principles applied:**
- Zero Trust — never trust, always verify
- Least-privilege access control
- IoT microsegmentation
- Continuous monitoring & uptime management

---

## 🏗️ Architecture
┌─────────────────────────────────────────┐
│           Proxmox VE Host               │
│                                         │
│  ┌──────────┐  ┌──────────┐             │
│  │Nextcloud │  │   n8n    │             │
│  │  (LXC)   │  │  (LXC)   │             │
│  └──────────┘  └──────────┘             │
│                                         │
│  ┌──────────────────────────┐           │
│  │   Netbird (Zero Trust)   │           │
│  │   ZTNA — No VPN needed   │           │
│  └──────────────────────────┘           │
└─────────────────────────────────────────┘
│
▼
AWS Cloud Layer
(EC2 · S3 · IAM)

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| Hypervisor | Proxmox VE |
| Containers | LXC |
| Zero Trust | Netbird |
| File Storage | Nextcloud |
| Automation | n8n |
| Monitoring | Proxmox built-in + manual alerting |
| Cloud | AWS (EC2, S3, IAM) |
| Scripting | Python (boto3), Bash |
| Network Analysis | Wireshark |
| Security | QRadar SIEM, CVE monitoring |

---

## 🛡️ Security Features

- **Zero Trust Network Access** via Netbird — device-level authentication, 
  no open ports exposed to internet
- **IoT microsegmentation** — isolated network zones per device type
- **Least-privilege IAM** — scoped AWS roles, no root access used
- **Snapshot scheduling** — automated recovery points
- **CVE monitoring** — daily threat feed review
- **OWASP Top 10** methodology applied to all hosted services

---

## 📊 Uptime & Performance

- **99%+ uptime** maintained across all services
- Proactive monitoring with alerting
- Snapshot-based disaster recovery tested regularly

---

## 📁 Repository Structure
zero-trust-homelab/
├── docs/
│   ├── proxmox-setup.md
│   ├── netbird-ztna.md
│   ├── nextcloud-deployment.md
│   └── network-diagram.png
├── monitoring/
│   └── alert-config.md
├── scripts/
│   └── snapshot-scheduler.sh
└── README.md

---

## 🚧 Roadmap

- [ ] Add network diagram (draw.io)
- [ ] Document Proxmox VM/LXC configuration
- [ ] Add Netbird ZTNA setup guide
- [ ] Add Wireshark capture examples
- [ ] Integrate with SOC lab scenarios

---

## 👤 Author

**Mustafa Talha Tuzsuz**  
Cybersecurity & Cloud Engineer - Dublin, Ireland  
[LinkedIn](https://linkedin.com/in/tuzsuz) • [Email](mailto:tuzsuz@pm.me)

