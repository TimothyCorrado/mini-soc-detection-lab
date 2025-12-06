<p align="center">
  <img src="https://img.shields.io/badge/Blue%20Team-Log%20Engineering-1f6feb?style=for-the-badge">
  <img src="https://img.shields.io/badge/Windows%20Security-Audit%20Policy-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Sysmon-Operational%20Visibility-purple?style=for-the-badge">
  <img src="https://img.shields.io/badge/PowerShell-Logging%20Enabled-darkgreen?style=for-the-badge">
</p>

# 🛡️ SOC Log Engineering Project  
**Tag:** `@SOC-7DAY-PROJECT`  
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

## ✅ Day 3 Completed – Log Ingestion (Security + Sysmon) (12/06/2025)  
**Tag:** `@SOC-DAY3-INGEST`

- Exported authentication activity (4624 + 4625) from the Splunk SIEM into CSV format  
- Exported Sysmon process creation events (EventCode 1) into CSV  
- Stored datasets under `/evidence/day03/` for use in parsing and detection engineering  
- Established a clean data pipeline from Windows → Splunk → CSV for analysis workflows

---

## ✅ Day 2 Completed – SIEM Setup (Splunk) (12/05/2025)  
**Tag:** `@SOC-DAY2-SIEMSETUP`

- Installed and configured **Splunk Enterprise** inside the Windows VM.
- Added Windows Event Log inputs:
  - **Security Log**
  - **PowerShell Operational Log**
  - **Sysmon Operational Log**
- Verified ingestion using:
  - Raw searches (`index=main`)
  - Source-based searches
  - tstats enumeration of event channels
- Exported event samples and dashboard evidence into `/evidence/day02/`.

Day 2 establishes the lab’s SIEM pipeline, enabling log parsing, threat hunting, and detection engineering in the coming days.

---

## ✅ Day 1 Completed – Log Setup & Baseline Configuration (12/04/2025)  
**Tag:** `@SOC-DAY1-LOGSETUP`

Successfully configured the foundational telemetry sources required for SOC detection engineering:

- Enabled Windows Security Audit Policy (Logon, Account Logon, Policy Change, Privilege Use, Object Access, Detailed Tracking)
- Installed Sysmon v15.x with a hardened XML configuration
- Enabled PowerShell Module Logging, Script Block Logging, and optional Transcription
- Generated and validated baseline events:
  - 4624 (Successful Logon)
  - 4625 (Failed Logon)
  - Sysmon Event ID 1 (Process Create)
  - PowerShell 4104 (Script Block Logging)
- Collected all Day-1 evidence into `/evidence/day01/`

System is now fully instrumented and ready for Day 2 (Log Parsing & Detection Engineering).

## 🧩 Day 1 – Log Setup & Baseline (Begins Tomorrow, 12/04/2025)
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