# Module 01 — Introduction to Splunk

## 🎯 Objective

Understand the fundamentals of Splunk, its role in security operations, basic SIEM concepts, and how Splunk can be used to search and investigate Windows Security events.

---

# 📚 What I Learned

## What is Splunk?

Splunk is a platform used to collect, search, analyze, monitor, and visualize machine-generated data such as logs and security events.

In cybersecurity environments, Splunk can be used as a SIEM platform to centralize security data and help SOC analysts investigate suspicious activity.

## What is SIEM?

SIEM stands for:

**Security Information and Event Management**

A SIEM collects security-related events from different systems and provides a central platform for searching, monitoring, detecting, and investigating activity.

Examples of data sources include:

- Windows systems
- Linux systems
- Firewalls
- Web servers
- Network devices
- Applications
- Authentication systems

## Splunk in a SOC

A simplified security monitoring workflow is:

Data Sources → Splunk → Search → Investigation → Detection → Response

Splunk allows security analysts to investigate large amounts of log data without manually checking every individual system.

---

# 🏗️ Basic Splunk Architecture

The basic Splunk concepts introduced in this module were:

## Forwarder

A Splunk component that collects data from a system and forwards it to Splunk.

## Indexer

Responsible for storing and indexing incoming data so that it can be searched efficiently.

## Search Head

The interface used by analysts to search and investigate Splunk data.

Simplified workflow:

Data Source → Forwarder → Indexer → Search Head → SOC Analyst

---

# 🔎 Hands-On Investigation

Splunk was already installed before beginning this module, so installation and setup were skipped.

The Splunk environment contained existing Windows Security data.

An initial search was performed:

index=*

This returned:

**2,029 events**

The data was then narrowed down to Windows Security events.

Search:

index=* sourcetype="WinEventLog:Security"

Result:

**1,580 events**

---

# 🧪 Event Analysis

The Windows Security events were grouped by EventCode to identify the most common event types.

Search:

index=* sourcetype="WinEventLog:Security"
| stats count by EventCode
| sort - count

The first five results observed were:

| Event Code | Count |
|---|---:|
| 5379 | 1,095 |
| 4798 | 316 |
| 4624 | 75 |
| 4672 | 67 |
| 4058 | 25 |

This demonstrated how SPL can transform a large collection of events into a useful summary.

---

# 🔐 Successful Logon Investigation

Event Code 4624 was investigated as a successful logon event.

One observed event contained:

- Account: `Divine-pc$`
- Domain: `Workgroup`
- Logon Type: `5`

Logon Type 5 represents a service logon.

The `$` at the end of `Divine-pc$` indicated that the account was a computer account rather than a normal human user account.

This demonstrated that not every successful authentication event represents a person manually logging into a computer.

---

# 👤 Interactive Logon Investigation

Interactive logons were investigated using Logon Type 2.

Search:

index=* sourcetype="WinEventLog:Security" Logon_Type=2

An observed event contained:

- Account: `Divine`
- Computer/Domain: `Divine-pc`
- Logon Type: `2`

Logon Type 2 represents an interactive logon.

---

# 📊 User Logon Count

The number of interactive logons for the `Divine` account was investigated.

Search:

index=* sourcetype="WinEventLog:Security" Logon_Type=2 Account_Name=Divine
| stats count

Result:

**20 interactive logon events**

---

# ⏱️ Timeline Investigation

The timestamps of the interactive logons were examined.

Search:

index=* sourcetype="WinEventLog:Security" Logon_Type=2 Account_Name=Divine
| table _time Account_Name Account_Domain Logon_Type
| sort _time

Observed time range:

**Earliest:** 2026-10-03 20:02:20.004

**Latest:** 2026-10-03 20:03:20.620

The investigation showed 20 interactive logon events within approximately one minute.

---

# 🧠 Key Concepts

- Splunk
- SIEM
- Security logs
- Events
- Hosts
- Sources
- Sourcetypes
- Event Codes
- Windows Security Event Logs
- Successful logons
- Interactive logons
- Logon Types
- SPL searches
- SPL statistics
- Basic timeline analysis

---

# 💻 SPL Commands Used

## Search all available indexes

index=*

## Filter Windows Security events

index=* sourcetype="WinEventLog:Security"

## Count events by EventCode

index=* sourcetype="WinEventLog:Security"
| stats count by EventCode
| sort - count

## Investigate interactive logons

index=* sourcetype="WinEventLog:Security" Logon_Type=2

## Count interactive logons for a specific account

index=* sourcetype="WinEventLog:Security" Logon_Type=2 Account_Name=Divine
| stats count

## Display and sort logon timestamps

index=* sourcetype="WinEventLog:Security" Logon_Type=2 Account_Name=Divine
| table _time Account_Name Account_Domain Logon_Type
| sort _time

---

# 🧪 Practical Skills

By completing this module, I practiced how to:

- Search Splunk data
- Identify Windows Security logs
- Filter events
- Group events using `stats`
- Investigate Windows Event Codes
- Identify successful logons
- Identify interactive logons
- Investigate account activity
- Count security events
- Examine event timestamps
- Build a basic security investigation from raw logs

---

# 🎯 Module Outcome

This module introduced the basic Splunk workflow:

**Search → Filter → Analyze → Investigate → Answer**

Instead of manually examining thousands of events, Splunk can be used to narrow large datasets into specific security questions.

The investigation started with:

**2,029 total events**

and narrowed the data down to:

**1,580 Windows Security events**

then:

**75 successful logon events**

and finally:

**20 interactive logons for the Divine account**

---

# 🚀 Next Module

## Module 02 — Understanding Splunk Data

Next, I will learn more deeply about:

- Events
- Fields
- Timestamps
- Hosts
- Sources
- Sourcetypes
- Indexes
- Event metadata

The goal is to understand how Splunk organizes security data before moving deeper into SPL and security investigations.

---

# #️⃣ Tags

#Splunk #Cybersecurity #SOC #SIEM #BlueTeam #SPL #SecurityOperations #ThreatDetection #IncidentResponse #CyberSecurityLearning
