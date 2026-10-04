# 🔎 Splunk Learning Roadmap

A hands-on journey to learn **Splunk**, master **SPL**, analyze security logs, build detections, investigate incidents, and develop practical SOC analyst skills.

> **Learn → Practice → Investigate → Detect → Document**

---

## 🎯 Goal

The goal of this roadmap is to build practical Splunk and SIEM skills through hands-on labs, security investigations, detection engineering, and real-world-style projects.

By the end, I should be able to:

- Understand SIEM and Splunk fundamentals
- Navigate and configure Splunk
- Ingest and analyze security logs
- Write Splunk Search Processing Language (SPL)
- Investigate suspicious activity
- Build security detections and alerts
- Create SOC dashboards
- Investigate simulated security incidents
- Map detections to MITRE ATT&CK
- Document practical Splunk/SOC projects

---

# 🗺️ Learning Roadmap

## 🟢 Phase 1 — Splunk Fundamentals

### Module 01 — Introduction to Splunk

- What is Splunk?
- What is a SIEM?
- Why organizations use SIEM platforms
- Splunk architecture
- Splunk components
- Explore the Splunk interface

### Module 02 — Understanding Splunk Data

- Events
- Fields
- Timestamps
- Hosts
- Sources
- Sourcetypes
- Indexes
- Event metadata

### Module 03 — Getting Data into Splunk

- Adding data
- Uploading log files
- Monitoring files
- Data inputs
- Understanding ingestion
- Verifying ingested events

### Module 04 — Searching in Splunk

- Basic searches
- Keywords
- Field-based searches
- Time ranges
- Search results
- Saving searches

---

# 🟡 Phase 2 — SPL

### Module 05 — SPL Fundamentals

Learn the foundations of Splunk Search Processing Language:

- `search`
- `table`
- `fields`
- `sort`
- `dedup`
- `stats`

### Module 06 — Filtering Events

- AND
- OR
- NOT
- Wildcards
- Exact matches
- Field filtering

### Module 07 — Statistics & Aggregation

Learn:

- `stats count`
- `stats count by`
- `stats values`
- `stats dc`

Use statistics to identify patterns in security data.

### Module 08 — Time-Based Analysis

Learn:

- `timechart`
- `bin`
- `earliest`
- `latest`

Analyze activity across time.

### Module 09 — Data Transformation

Learn:

- `eval`
- `rename`
- `fields`
- `table`
- `sort`

Create useful fields and organize investigation results.

### Module 10 — Regular Expressions & Field Extraction

Learn:

- `rex`

Extract useful information from raw events.

### Module 11 — Advanced SPL

Combine multiple commands to create more powerful investigations.

Example:

`search → eval → stats → sort → table`

---

# 🟠 Phase 3 — Security Log Analysis

### Module 12 — Authentication Logs

Analyze:

- Failed logins
- Successful logins
- User accounts
- Source IPs
- Authentication patterns

### Module 13 — Windows Security Logs

Investigate:

- Windows authentication
- Account activity
- Security events
- Privilege-related activity
- Process creation

### Module 14 — Linux Security Logs

Analyze:

- SSH authentication
- Failed login attempts
- Successful logins
- User activity
- Authentication failures

### Module 15 — Web & Network Logs

Analyze:

- HTTP requests
- Source IPs
- Status codes
- User agents
- Suspicious requests
- Network activity

### Module 16 — Process & Command-Line Analysis

Investigate:

- Process creation
- Command-line arguments
- Parent/child processes
- Suspicious processes
- Script execution

---

# 🔴 Phase 4 — Threat Detection

### Module 17 — Brute-Force Detection

Build a detection for repeated authentication failures.

Multiple failed logins  
↓  
Same source IP  
↓  
Short time period  
↓  
🚨 Possible brute-force attack

### Module 18 — Suspicious Login Detection

Investigate:

- Unusual login times
- Multiple source IPs
- Repeated authentication failures
- Unusual account activity

### Module 19 — Suspicious PowerShell Activity

Analyze PowerShell events and identify potentially suspicious command execution.

### Module 20 — Account Compromise Detection

Investigate scenarios involving:

- Repeated failed authentication
- Successful login
- New source IP
- Privileged activity
- Suspicious actions after authentication

### Module 21 — Detection Engineering

Learn how to transform suspicious behavior into detection logic.

Data  
↓  
Search  
↓  
Detection Logic  
↓  
Alert  
↓  
Investigation

---

# 🟣 Phase 5 — Alerts & SOC Dashboards

### Module 22 — Splunk Alerts

Learn:

- Alert conditions
- Thresholds
- Scheduling
- Trigger actions
- Alert investigation

### Module 23 — SOC Dashboards

Build dashboards showing:

- Total events
- Failed logins
- Successful logins
- Top source IPs
- Top users
- Events over time
- Security alerts

### Module 24 — Investigation Dashboards

Create panels for:

- Authentication activity
- Suspicious IPs
- Failed login trends
- Process activity
- Security detections

---

# 🔵 Phase 6 — Incident Response

### Module 25 — Alert Triage

Learn how to evaluate an alert:

- What happened?
- Who was involved?
- When did it happen?
- Where did it originate?
- Is the activity expected?
- What happened before and after?

### Module 26 — Timeline Analysis

Build an incident timeline from Splunk events.

Initial activity  
↓  
Authentication  
↓  
Execution  
↓  
Persistence  
↓  
Other activity

### Module 27 — Incident Investigation

Perform complete investigations using:

- SPL
- Logs
- Dashboards
- Alerts
- Event timelines
- Evidence

### Module 28 — MITRE ATT&CK Mapping

Map observed behavior to relevant MITRE ATT&CK techniques.

Example:

Brute Force  
↓  
MITRE ATT&CK  
↓  
T1110

---

# ⚫ Phase 7 — Practical Projects

### Project 01 — Authentication Log Analyzer

Analyze authentication activity and identify:

- Failed logins
- Successful logins
- Top users
- Top source IPs
- Suspicious patterns

### Project 02 — Brute-Force Detection Lab

Build a complete detection for repeated authentication attempts.

Include:

- SPL query
- Detection logic
- Alert
- Investigation
- Findings

### Project 03 — SOC Dashboard

Build a dashboard for monitoring authentication and security activity.

### Project 04 — Suspicious PowerShell Investigation

Investigate simulated PowerShell activity and determine whether the behavior is suspicious.

### Project 05 — Full Incident Investigation

Investigate a simulated compromise from:

Initial Activity  
↓  
Detection  
↓  
Triage  
↓  
Investigation  
↓  
Timeline  
↓  
MITRE ATT&CK  
↓  
Findings  
↓  
Response

---

# 🧰 Tools

- Splunk
- Windows Event Logs
- Linux Logs
- SPL
- MITRE ATT&CK
- Virtual Machines
- Security Datasets
- Home Lab

---

# 📂 Documentation Structure

Each module can contain:

Module-01/  
├── README.md  
├── notes/  
└── queries/

Projects can contain:

Project/  
├── README.md  
├── queries/  
├── detections/  
├── dashboards/  
└── evidence/

---

# 📈 Skills Checklist

- [ ] Understand SIEM fundamentals
- [ ] Navigate Splunk
- [ ] Understand Splunk data
- [ ] Ingest security logs
- [ ] Search and filter events
- [ ] Write SPL queries
- [ ] Use SPL statistics
- [ ] Analyze authentication logs
- [ ] Investigate Windows logs
- [ ] Investigate Linux logs
- [ ] Analyze network/web logs
- [ ] Detect brute-force attacks
- [ ] Analyze suspicious processes
- [ ] Investigate PowerShell activity
- [ ] Create Splunk alerts
- [ ] Build SOC dashboards
- [ ] Perform incident investigations
- [ ] Map activity to MITRE ATT&CK
- [ ] Document security investigations

---

## 🚀 Final Goal

Don't just learn how to **use Splunk**.

Learn how to use Splunk to:

**Find → Investigate → Detect → Explain → Document**

suspicious activity in a security environment.
