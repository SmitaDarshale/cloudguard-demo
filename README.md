# TENEX CloudGuard — AWS Security Command Center

> A browser-based interactive security operations dashboard that simulates AI-powered cloud threat detection, triage, and response — inspired by [TENEX.ai](https://tenex.ai)'s MDR platform.

**Built by:** Smita Darshale | [linkedin.com/in/darshalesmita](https://www.linkedin.com/in/darshalesmita)

---

## Overview

This project is a fully interactive, single-file web application that simulates what an AI-native Security Operations Center (SOC) looks like in practice. It ingests realistic AWS cloud security alerts, scores them using a multi-factor AI triage model, and enables analysts to take immediate remediation action — all in real time from the browser.

No backend, no dependencies, no installation required. Built with pure HTML, CSS, and Chart.js.

---

## Live Demo

Host it yourself in under 5 minutes:

1. Upload `index.html` to a GitHub repository
2. Enable GitHub Pages (Settings → Pages → main branch)
3. Access at `https://yourusername.github.io/cloudguard-demo`

---

## Features

### Metric Cards
Four summary KPIs displayed at the top of the dashboard, directly mirroring TENEX.ai's core value proposition:

| Metric | Value | Context |
|---|---|---|
| Total alerts | 12 | Last 24 hours |
| Critical / High | 4 | Needs immediate action |
| Avg triage time | 1m 42s | vs industry average of 38 minutes |
| False positives | 2% | 98% eliminated by AI scoring |

---

### Alert Feed
A live-updating panel of 9 realistic AWS security alerts, each modeled on real-world cloud threat scenarios:

- IAM privilege escalation
- Unusual S3 data exfiltration
- EC2 cryptomining detected
- CloudTrail logging disabled
- Security group SSH open to 0.0.0.0/0
- VPC flow log anomaly (lateral movement)
- GuardDuty port scan detection
- Root account login detected
- Unused IAM access key (90+ days)

Each alert displays:
- **Severity badge** — Critical / High / Medium / Low
- **Source service** — the AWS service that fired the alert
- **Region** — AWS region affected
- **Time** — how long ago the alert fired

**Filter buttons** allow analysts to narrow the view by severity level (All / Critical / High / Medium).

---

### 24-Hour Alert Volume Chart
A dual-series bar chart (Chart.js) showing alert activity across the last 24 hours:

- **Blue bars** — total alert volume per hour
- **Red bars** — critical-only alert volume per hour
- Simulates realistic traffic patterns: quiet overnight, spikes during business hours

---

### AI Triage Engine
The centerpiece of the application. Clicking any alert instantly runs a multi-factor risk analysis and renders a full triage report.

#### Risk Score (0–100)
A single composite score color-coded by severity:

| Score range | Color | Severity |
|---|---|---|
| 85–100 | Red | Critical |
| 65–84 | Amber | High |
| 45–64 | Blue | Medium |
| 0–44 | Green | Low |

#### Four Scoring Factors
Each factor is scored independently out of 100 and visualized with a color-coded progress bar:

| Factor | Description |
|---|---|
| **Likelihood** | Probability this is a real threat vs noise |
| **Impact** | Potential damage if the threat is confirmed |
| **Exposure** | Blast radius — how widely the environment is affected |
| **Velocity** | How fast the threat is moving or escalating |

#### AI Recommendation
Detailed, context-specific remediation guidance for each alert type. Examples:

- *IAM escalation:* Explains the attack pattern, correlates with prior MFA failures, recommends immediate role revocation
- *S3 exfiltration:* Identifies the external IP, names the affected buckets, recommends IP block and bucket policy audit
- *EC2 cryptomining:* References the specific instance ID, recommends forensic snapshot before termination
- *CloudTrail disabled:* Flags this as a known attacker evasion technique, recommends re-enabling and auditing the gap window

#### Action Buttons
Three context-aware actions per alert:

- **Primary action** — specific to the threat type (e.g. "Revoke IAM Role", "Block & Isolate", "Terminate Instance")
- **Assign to analyst** — escalation workflow simulation
- **Dismiss as false positive** — feedback loop that would make the AI model smarter over time

Each button fires a toast notification confirming the action was dispatched.

---

### Threat Intelligence Charts

#### Threat Category Breakdown (7 days)
Horizontal bar chart showing the distribution of attack types:

| Category | Share |
|---|---|
| IAM Anomaly | 34% |
| Network Intrusion | 27% |
| Data Exfiltration | 18% |
| Malware | 13% |
| Config Drift | 8% |

#### Severity Trend (7 days)
Multi-line chart tracking daily alert volumes across Critical, High, and Medium severity — useful for identifying attack campaign patterns or unusual spikes.

---

## AWS Services Covered

The alerts and triage logic reference real AWS security tooling:

| AWS Service | Role in this project |
|---|---|
| **AWS GuardDuty** | Threat detection (cryptomining, port scans, exfiltration) |
| **AWS CloudTrail** | API activity logging (IAM escalation, root login, logging disabled) |
| **AWS Config** | Configuration compliance (security group misconfiguration) |
| **AWS VPC Flow Logs** | Network traffic analysis (lateral movement detection) |
| **AWS IAM** | Identity and access management (unused keys, privilege escalation) |

---

## Technology Stack

| Technology | Usage |
|---|---|
| HTML5 | Application structure |
| CSS3 | Styling, animations, responsive layout |
| Vanilla JavaScript | Alert data, triage logic, interactivity |
| [Chart.js 4.4.1](https://www.chartjs.org/) | Bar charts, line charts (via cdnjs CDN) |

No frameworks. No build tools. No backend. Single file deployment.

---

## Project Structure

```
index.html          # Complete application — styles, markup, and logic in one file
README.md           # This file
```

---

## How This Connects to Real Cloud Security Experience

This project was built to demonstrate practical cloud and security knowledge, not just frontend skills. Every element maps to real hands-on experience:

| Project feature | Real-world experience |
|---|---|
| AWS GuardDuty / CloudTrail alerts | AWS infrastructure work at Cerner (2021–2022) |
| Security hardening & compliance | Twistlock, HIPAA/PHI compliance at Cerner & Oracle |
| Infrastructure monitoring & observability | Grafana, Splunk, Dynatrace at Oracle America |
| Incident response & RCA | Production support engineering at TCS & Oracle |
| Cloud architecture & migrations | AWS-to-OCI migration leadership at Cerner |
| Multi-cloud environment knowledge | AWS, OCI, Azure across multiple roles |

---

## About the Developer

**Smita Darshale** Software Engineer at Oracle, I contribute to enhancing system security and stability through vulnerability management and cloud infrastructure solutions. My work includes identifying and resolving CVEs, analyzing dependencies, upgrading vulnerable components, and ensuring compliance through security scans using tools like Twistlock. My focus extends to building and maintaining scalable systems that prioritize security and reliability. 

At Oracle, I support production by troubleshooting issues using tools like Hadoop workflows and Splunk logs, while addressing incidents and ensuring smooth service operation. My expertise includes developing Java-based microservices, contributing to public APIs, and designing infrastructure with Terraform for deployment on cloud environments like Oracle Cloud Infrastructure (OCI). My commitment lies in improving system security, enabling clean architecture, and fostering innovation through continuous learning.

- Email: smita.darshale@gmail.com
- Phone: +1-913-244-6313
- Location: Olathe, KS
- LinkedIn: [linkedin.com/in/darshalesmita](https://www.linkedin.com/in/darshalesmita)

---

## Inspiration

Built as a portfolio project inspired by [TENEX.ai](https://tenex.ai) — an AI-native, human-led Managed Detection & Response (MDR) provider that uses domain-specific AI models to triage every alert, investigate every threat, and free security teams for strategic work.

---

*This is a demonstration project using simulated data. No real AWS environments or credentials are involved.*
