# SOC Alert Automation 🚨🤖

This project demonstrates a Security Operations Center (SOC) setup with **automated alert processing** using:

- ✅ Wazuh (SIEM)
- ✅ TheHive (Case Management)
- ✅ Shuffle (Security Automation)

Alerts such as *Mimikatz detections* from Wazuh are forwarded to Shuffle workflows, parsed, enriched using VirusTotal, and converted into actionable TheHive cases.

---

## 📌 Architecture Overview

<!-- ![SOC Alert Automation Diagram](./docs/soc-architecture.png) -->

**Components:**

- **Wazuh**: Generates alerts (e.g., credential dumping, network threats).
- **Shuffle**: Receives alerts via webhook, processes them, adds context, and pushes to TheHive.
- **TheHive**: Receives enriched alerts and automatically creates a alerts with severity, tags, and MITRE mappings.

---

## 🛠 Tools Used

| Tool         | Purpose                                | Installation Mode         |
|--------------|-----------------------------------------|----------------------------|
| Wazuh        | Log Monitoring & Detection              | Installed via bash script |
| TheHive      | Case Management                         | Installed natively (non-Docker) |
| Shuffle.io   | Workflow Automation                     | Cloud-hosted              |
| VirusTotal API | Threat Intelligence Enrichment        | Integrated in Shuffle     |
| UFW          | Firewall for secure access              | Configured manually       |
| Cloudflare Tunnel | Public access to TheHive           | For Shuffle API Authentication  |

---
```bash 
📂 SOC-Alert-Automation/
├── 📁 docs/
├   └── 📁 Wazuh                            # Wazuh Images
│   └── 📁 Shuffle                          # Shuffle Images
│   └── 📁 Hive                             # TheHive Images
├── 📁 scripts/
│   ├── 📄 install-wazuh.sh                 # Setup script for Wazuh
│   ├── 📄 install-thehive.sh               # Full setup for TheHive 5.2 and dependencies
│   └── 📄 ufw-rules.sh                     # Example firewall rules for SOC
├── 📄 README.md                            # Project overview, architecture, usage
```