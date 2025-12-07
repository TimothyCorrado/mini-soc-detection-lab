<p align="center">
  <img src="https://img.shields.io/badge/Blue%20Team-Log%20Engineering-0a84ff?style=for-the-badge&logo=windows&logoColor=white">
  <img src="https://img.shields.io/badge/Windows%20Security-Audit%20Policy-004aad?style=for-the-badge&logo=microsoft&logoColor=white">
  <img src="https://img.shields.io/badge/Sysmon-Process%20Monitoring-5a32a3?style=for-the-badge&logo=security&logoColor=white">
  <img src="https://img.shields.io/badge/PowerShell-Operational%20Logging-066cfa?style=for-the-badge&logo=powershell&logoColor=white">
</p>

# ️ SOC Log Engineering Project

**Tag:** `@SOC-7DAY-PROJECT`  
**Purpose:** Build a mini SOC detection lab around a Windows VM, Sysmon, Splunk, and (later) Wazuh to showcase blue-team log engineering and detection skills.

This project is about doing what real SOC engineers do every day:

- Turning Windows into a proper telemetry source
- Wiring that telemetry into a SIEM
- Exporting and shaping data for detections and investigations
- Documenting each step so a hiring manager can follow the story

---

## Scope

This lab focuses on practical, host-centric detection engineering:

- Configuring **Windows Security Audit Policy**
- Deploying **Sysmon** with a hardened XML configuration
- Enabling **PowerShell** operational logging
- Generating clean baseline events:
  - 4624 / 4625 (logon activity)
  - Sysmon Event ID 1 (process creation)
  - PowerShell 4104 (ScriptBlock logging)
- Ingesting logs into a **SIEM (Splunk)** and exporting datasets for analysis
- Laying the groundwork to add **Wazuh** as an additional detection surface later

Work is structured as “Day 1 – Day 7” so each commit shows clear forward progress.

---

### 🛡️ Day 5 – Alert Triage & Investigation — 12/06/2025
**Tag:** `@SOC-DAY5-TRIAGE`   

**Focus:** Perform SOC-style triage on a triggered brute-force detection alert.

#### ✔ Key Accomplishments
- Triggered the excessive failed logons detection (4625)
- Captured evidence and screenshots of the alert in Splunk
- Performed a full Tier 1 → Tier 2 investigation workflow
- Documented triage questions, enrichment steps, and results
- Assessed alert severity and closed as benign based on findings
- Added MITRE ATT&CK mapping (T1110 – Brute Force)

#### 📁 Evidence
- Alert screenshots and triage artifacts saved in: `evidence/day05/`
- Full investigation documented in: `day05-triage.md`

**Result:**  
Day 5 establishes a real SOC triage workflow using Windows Security telemetry, enabling investigation reasoning, correlation queries, and ATT&CK-aligned alert classification.

---

## ✅ Day 4 – Detection Engineering (Security + Sysmon) — 12/06/2025
**Tag:** `@SOC-DAY4-DETECTIONS`  

**Focus:** Convert raw Windows Security + Sysmon telemetry into actionable detections using Splunk SPL.

### 🔍 Detections Implemented
- **Excessive Failed Logons (Brute Force):**  
  SPL rule analyzing 4625 failures over 5-minute windows.
- **Success After Multiple Failures:**  
  Correlates failed (4625) and successful (4624) logons to detect spray-success behavior.
- **Sysmon Operational Visibility:**  
  Baseline query confirming ingestion of Sysmon Operational events into Splunk.
- **Sysmon LOLBins Detection:**  
  Prepared SPL to identify execution of high-risk native Windows binaries (cmd, powershell, mshta, certutil, bitsadmin, wscript).

### 📁 Deliverables
- All SPL queries saved under:  
  `evidence/day04/*.spl`
- Screenshots and CSV exports stored under:  
  `evidence/day04/`
- Full write-up documented in:  
  `day04-detections.md`

**Outcome:**  
Day 4 establishes the first detection layer of the SOC lab, enabling authentication anomaly detection and validating Sysmon telemetry for future threat behavior analysis.

---

## ✅ Day 3 – Log Ingestion (Security + Sysmon) — 12/06/2025

**Tag:** `@SOC-DAY3-INGEST`

- Exported authentication activity (4624 + 4625) from Splunk into CSV
- Exported Sysmon process creation events (EventCode 1) from the Sysmon Operational channel
- Stored datasets under `/evidence/day03/`:
  - `splunk_security_logons_7d.csv`
  - `splunk_sysmon_eventcode1_7d.csv`
- Established a clean pipeline: **Windows → Splunk → CSV** for analysis and detection-building

See: `day03-ingest.md`

---

## ✅ Day 2 – SIEM Setup (Splunk) — 12/05/2025

**Tag:** `@SOC-DAY2-SIEMSETUP`

- Installed and configured **Splunk Enterprise** inside the Windows VM
- Added Windows Event Log inputs:
  - Security Log
  - PowerShell Operational Log (configured)
  - Sysmon Operational Log
- Verified ingestion using:
  - Raw searches (`index=main`)
  - Source-based searches
  - `tstats` enumeration of event channels
- Exported event samples and evidence to `/evidence/day02/`:
  - `inputs.conf`
  - Security log screenshots and CSVs
  - Sysmon screenshots and CSVs

Day 2 turned the VM into a **mini SIEM environment** that can be used for threat hunting and detection engineering.

See: `day02-siem-setup.md`

---

## ✅ Day 1 – Log Setup & Baseline Configuration — 12/04/2025

**Tag:** `@SOC-DAY1-LOGSETUP`

Baseline host instrumentation:

- Enabled Windows Security Audit Policy:
  - Logon, Account Logon, Policy Change, Privilege Use, Object Access, Detailed Tracking
- Installed **Sysmon v15.x** with a hardened XML config
- Enabled PowerShell:
  - Module Logging
  - Script Block Logging
  - (Optional) Transcription
- Generated and validated baseline events:
  - 4624 (successful logon)
  - 4625 (failed logon)
  - Sysmon Event ID 1 (ProcessCreate)
  - PowerShell 4104 (ScriptBlock)

Day 1 output is stored under `/evidence/day01/` and documented in `day01-log-setup.md`.

---

## Repository Structure

```text
.
├── README.md                      # Project overview and day-by-day progress
├── day01-log-setup.md             # Day 1 – Windows logging baseline
├── day02-siem-setup.md            # Day 2 – Splunk SIEM setup & inputs
├── day03-ingest.md                # Day 3 – Dataset export from Splunk
├── detections/                    # (Planned) SPL rules / sigma-style logic
├── diagrams/                      # Architecture / data flow diagrams
├── triage_notes/                  # (Planned) Investigation / triage walkthroughs
└── evidence/
    ├── day01/                     # Audit policy exports, Sysmon config, baseline screenshots
    ├── day02/                     # Splunk inputs.conf, SIEM screenshots, CSV exports
    └── day03/                     # Security + Sysmon CSV datasets for analysis
