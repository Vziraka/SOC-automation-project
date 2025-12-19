# 🛡️ SOC Automation Project – Splunk, n8n, ChatGPT & Slack

## 📌 Project Overview
This project demonstrates a **SOC automation pipeline** that detects suspicious Windows login activity, enriches alerts with threat intelligence, summarizes them using AI, and delivers actionable notifications to Slack.

## 🧠 What This Project Does
- Ingests Windows Security logs into **Splunk**
- Detects failed login attempts (**Event ID 4625**)
- Triggers alerts via **Splunk Webhooks**
- Automates handling with **n8n**
- Uses **ChatGPT** for alert summarization and severity assessment
- Enriches IPs using **AbuseIPDB**
- Sends structured alerts to **Slack**

## 🧰 Technologies Used
- Splunk Enterprise (SIEM)
- Splunk Universal Forwarder
- n8n (Dockerized)
- Docker & Docker Compose
- ChatGPT API
- AbuseIPDB API
- Slack API
- VMware
- Windows 10, Ubuntu, Kali Linux

## 🏗️ Lab Environment
| Machine | Purpose |
|---|---|
| Windows 10 VM | Log generation |
| Ubuntu VM | Splunk Enterprise |
| Ubuntu VM | n8n Automation |
| Kali Linux | Security testing |
| Host | Management & SSH |

## 🔄 Architecture Flow
```
Windows Logs → Splunk → Alert (4625) → Webhook → n8n
   ├─ ChatGPT (Summary & Severity)
   ├─ AbuseIPDB (IP Enrichment)
   ↓
 Slack Alerts
```

## ⚙️ Setup Summary
### Splunk
- Enabled receiving on port **9997**
- Installed Windows Add-on
- Created alert for failed logins:
```spl
index="mydfir-project" EventCode=4625
| stats count by _time, ComputerName, user, src_ip
```

### n8n
- Deployed via Docker Compose
- Webhook listener → ChatGPT → AbuseIPDB → Slack

## 🤖 AI Alert Analysis
ChatGPT acts as a Tier 1 SOC assistant to:
- Summarize alerts
- Map to MITRE ATT&CK concepts
- Assign severity
- Recommend next actions

## 🌐 Threat Intelligence
- IP enrichment using **AbuseIPDB**
- Results passed to AI for context-aware analysis

## 📣 Slack Integration
- Slack App with OAuth scopes
- Alerts delivered to a dedicated channel

## 📸 Screenshots
> Place images in `/screenshots` and update filenames below.

### Splunk Failed Login Alert
![Splunk Alert](screenshots/splunk_failed_login_alert.png)

### n8n Automation Workflow
![n8n Workflow](screenshots/n8n_soc_workflow.png)

### Slack Alert Output
![Slack Alert](screenshots/slack_alert_output.png)

## 🎯 Skills Demonstrated
- SIEM alerting
- Security automation
- API integrations
- Threat intel enrichment
- SOC workflow design

## 🚀 Future Improvements
- Add VirusTotal enrichment
- Severity-based routing
- Automated containment actions

## 👤 Author
**Ensizziyo Ziraka**
