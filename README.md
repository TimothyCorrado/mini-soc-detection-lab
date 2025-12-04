<p align="center">
  <img src="https://img.shields.io/badge/Blue%20Team-Log%20Engineering-1f6feb?style=for-the-badge">
  <img src="https://img.shields.io/badge/Windows%20Security-Audit%20Policy-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Sysmon-Operational%20Visibility-purple?style=for-the-badge">
  <img src="https://img.shields.io/badge/PowerShell-Logging%20Enabled-darkgreen?style=for-the-badge">
</p>

# 🛡️ SOC Log Engineering Project  
**Tag:** `@SOC-DAY1-LOGSETUP`  
**Purpose:** Build a production-grade Windows logging baseline for SOC detection engineering.

This project establishes the foundation of a SIEM-ready telemetry pipeline inside a controlled Windows VM.  
The focus is on correct configuration, artifact generation, and repeatable processes used in real SOC environments.

---

## 📘 Scope
This project demonstrates practical blue-team capabilities:

- Configuring Security Audit Policies  
- Deploying Sysmon with hardened XML  
- Enabling PowerShell operational logging  
- Generating clean baseline authentication events (4624 / 4625)  
- Capturing and exporting logs for later parsing and detection writing  

The work is structured into daily, documented deliverables aligned with SOC workflows.

---

## 🧩 Day 1 – Log Setup & Baseline (Begins Tomorrow)
Day 1 will produce employer-ready artifacts including:

- `audit_policy_export.txt`  
- `powershell_logging_status.txt`  
- `sysmon_config.xml`  
- `event-viewer-baseline.png`  
- A documented baseline validation (4624, 4625, Sysmon ID 1, PowerShell 4104)

These files demonstrate control over Windows telemetry and your ability to prepare systems for detection engineering.

---

## 📁 Repository Structure (Initial)
/evidence/
/day01/ # Will contain exported logs and screenshots
day01-log-setup.md # Technical notes and validation steps
README.md

---

## 📅 Today’s Commit
This commit initializes the project structure and documentation required for Day 1:

- Added project summary focused on SOC relevance  
- Created evidence directory structure  
- Added Day 1 documentation file placeholder  

This establishes the repository as a clean audit trail of your SOC engineering workflow.

---

## 🔜 Next Deliverables
Starting tomorrow, this repo will include:

- A validated Windows audit policy configuration  
- Sysmon installation and event verification  
- PowerShell logging configuration and event verification  
- Baseline authentication artifacts  
- Evidence ready for parsing, detection-building, and dashboard creation  

These deliverables will be used to build real detections, enrichment logic, and incident simulation in later phases.

---