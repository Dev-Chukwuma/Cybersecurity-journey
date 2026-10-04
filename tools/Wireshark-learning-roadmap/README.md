# 🦈 Wireshark Learning Roadmap

A hands-on journey to learn **Wireshark**, master packet analysis, investigate network traffic, identify suspicious activity, and connect network visibility with Blue Team, Red Team, and Purple Team operations.

> **Capture → Filter → Analyze → Investigate → Detect → Document**

---

# 🎯 Goal

The goal of this roadmap is to develop practical network analysis skills using Wireshark.

By the end, I should be able to:

- Understand packet capture and network traffic
- Understand Ethernet, TCP/IP, UDP, DNS, HTTP, HTTPS, and common protocols
- Capture network traffic
- Apply Wireshark display filters
- Follow network conversations
- Analyze TCP connections
- Investigate DNS traffic
- Analyze HTTP traffic
- Identify suspicious network behavior
- Investigate authentication traffic
- Detect network reconnaissance
- Analyze malware-related traffic in controlled environments
- Extract indicators of compromise
- Investigate security incidents using packet captures
- Connect packet analysis with SIEM investigations
- Document network security investigations

---

# 🗺️ Learning Roadmap

# 🟢 Phase 1 — Network Fundamentals

## Module 01 — Introduction to Wireshark

Learn:

- What is Wireshark?
- What is packet analysis?
- What is packet capture?
- Why security analysts use Wireshark
- Wireshark interface
- Capture vs display filters
- Packet details
- Packet bytes

---

## Module 02 — Networking Fundamentals

Review:

- OSI model
- TCP/IP model
- Ethernet
- MAC addresses
- IP addresses
- Ports
- Protocols
- Packets
- Frames
- Segments
- Network conversations

---

## Module 03 — Ethernet & ARP

Learn:

- Ethernet frames
- MAC addresses
- ARP
- ARP requests
- ARP replies
- ARP tables
- ARP anomalies
- ARP spoofing concepts

Practice identifying normal ARP traffic.

---

## Module 04 — IP Traffic

Learn:

- IPv4
- IPv6
- Source IP
- Destination IP
- TTL
- Protocol fields
- Fragmentation
- ICMP

Practice identifying hosts communicating across a network.

---

# 🟡 Phase 2 — TCP & UDP Analysis

## Module 05 — TCP Fundamentals

Learn:

- TCP connections
- SYN
- SYN-ACK
- ACK
- FIN
- RST
- TCP flags
- Sequence numbers
- Acknowledgements
- TCP ports

---

## Module 06 — TCP Three-Way Handshake

Analyze:

Client  
↓  
SYN  
↓  
Server  
↓  
SYN-ACK  
↓  
Client  
↓  
ACK  
↓  
Connection Established

Learn how to identify successful and failed TCP connections.

---

## Module 07 — TCP Troubleshooting

Investigate:

- Retransmissions
- Duplicate ACKs
- TCP resets
- Connection failures
- Packet loss
- Timeouts
- Slow connections

---

## Module 08 — UDP Analysis

Learn:

- UDP characteristics
- UDP ports
- DNS traffic
- DHCP traffic
- Connectionless communication
- UDP-based attacks
- Suspicious UDP traffic

---

# 🟠 Phase 3 — Wireshark Filters & Analysis

## Module 09 — Display Filters

Learn common filters such as:

- ip.addr
- ip.src
- ip.dst
- tcp
- udp
- icmp
- dns
- http
- tls

Learn how to combine filters using:

- AND
- OR
- NOT

---

## Module 10 — Advanced Filtering

Learn how to filter by:

- Ports
- Protocols
- IP addresses
- TCP flags
- Packet lengths
- DNS queries
- HTTP methods
- HTTP status codes
- Specific fields

---

## Module 11 — Following Network Conversations

Learn:

- Follow TCP Stream
- Follow UDP Stream
- Stream reconstruction
- Client/server communication
- Conversation analysis

Use reconstructed conversations to understand what happened during a network session.

---

## Module 12 — Conversations & Endpoints

Learn how to identify:

- Top communicating hosts
- Source endpoints
- Destination endpoints
- TCP conversations
- UDP conversations
- Network volume
- Suspicious communication patterns

---

## Module 13 — Statistics & Protocol Analysis

Explore:

- Protocol hierarchy
- Conversations
- Endpoints
- I/O graphs
- Packet lengths
- Network throughput
- Protocol distribution

Use statistics to quickly understand a packet capture.

---

# 🔴 Phase 4 — Protocol Analysis

## Module 14 — DNS Analysis

Investigate:

- DNS queries
- DNS responses
- Domain names
- Query types
- Response codes
- Suspicious domains
- High-volume DNS activity
- DNS tunneling concepts

---

## Module 15 — HTTP Analysis

Analyze:

- HTTP requests
- HTTP responses
- GET
- POST
- Headers
- Cookies
- User agents
- Status codes
- URLs
- Parameters

Understand what normal and suspicious HTTP traffic looks like.

---

## Module 16 — HTTPS & TLS

Learn:

- TLS fundamentals
- TLS handshake
- Certificates
- Encrypted traffic
- SNI
- TLS versions
- Encryption limitations
- What Wireshark can and cannot reveal from encrypted traffic

---

## Module 17 — DHCP Analysis

Investigate:

- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP ACK
- Client identification
- Assigned IP addresses
- Suspicious DHCP behavior

---

## Module 18 — ICMP Analysis

Analyze:

- Echo requests
- Echo replies
- Ping traffic
- ICMP errors
- Network discovery
- Suspicious ICMP activity

---

# 🟣 Phase 5 — Security Analysis

## Module 19 — Network Reconnaissance

Detect:

- Port scanning
- Host discovery
- Service discovery
- Repeated connection attempts
- SYN scanning
- Unusual connection patterns

Understand how reconnaissance appears in packet captures.

---

## Module 20 — Brute-Force Traffic Analysis

Investigate:

- Repeated authentication attempts
- SSH traffic
- HTTP login attempts
- RDP-related traffic
- Authentication patterns
- Source IP behavior

Connect packet activity with authentication logs.

---

## Module 21 — Suspicious HTTP Traffic

Investigate:

- Suspicious URLs
- Strange user agents
- Unusual HTTP methods
- Large requests
- Repeated requests
- Suspicious parameters
- Web attack traffic

---

## Module 22 — Credential Exposure Investigation

Investigate controlled packet captures containing insecure authentication traffic.

Learn:

- Plaintext protocols
- HTTP credentials
- FTP credentials
- Telnet traffic
- Credential exposure
- Secure alternatives

Understand why encrypted protocols are important.

---

## Module 23 — Malware Traffic Analysis

Using safe, controlled datasets, investigate:

- Command-and-control concepts
- Beaconing
- Suspicious DNS
- Suspicious HTTP
- Repeated outbound connections
- Unusual destinations
- Network indicators of compromise

---

## Module 24 — Data Exfiltration Analysis

Learn how suspicious data transfer may appear in network traffic.

Investigate:

- Large outbound transfers
- Unusual destinations
- Repeated data transfers
- Unusual protocols
- DNS-based exfiltration concepts
- Timing patterns

---

# ⚫ Phase 6 — Incident Investigation

## Module 25 — Packet Capture Investigation

Learn a structured investigation process:

Capture  
↓  
Filter  
↓  
Identify Hosts  
↓  
Identify Protocols  
↓  
Follow Conversations  
↓  
Find Suspicious Activity  
↓  
Extract Indicators  
↓  
Document Findings

---

## Module 26 — Network Timeline Analysis

Build a timeline from packet captures.

Identify:

- Initial connection
- Reconnaissance
- Authentication
- Exploitation
- Command execution
- Outbound communication
- Data transfer
- Connection termination

---

## Module 27 — Indicators of Compromise

Extract:

- IP addresses
- Domains
- URLs
- Ports
- Protocols
- User agents
- File hashes where available
- Suspicious network patterns

Document indicators for further investigation.

---

## Module 28 — Wireshark + Splunk Investigation

Connect network analysis with SIEM investigation.

Workflow:

Network Activity  
↓  
Wireshark  
↓  
Identify Indicators  
↓  
Splunk Search  
↓  
Correlate Logs  
↓  
Build Timeline  
↓  
Investigate Incident  
↓  
Document Findings

---

# 🟣 Phase 7 — Purple Team Applications

## Module 29 — Attack Traffic Analysis

Perform controlled attacks inside a lab environment and capture the resulting traffic.

Examples:

- Network scanning
- Web requests
- Authentication attempts
- DNS activity
- Controlled exploitation

Then analyze the resulting traffic using Wireshark.

---

## Module 30 — Purple Team Network Investigation

Complete a full attack-and-detection exercise.

Scenario:

Red Team Activity  
↓  
Network Traffic  
↓  
Wireshark Capture  
↓  
Traffic Analysis  
↓  
Indicators Identified  
↓  
Splunk Investigation  
↓  
MITRE ATT&CK Mapping  
↓  
Detection Improvement  
↓  
Retest

Document the complete investigation.

---

# 🧪 Practical Projects

# Project 01 — Network Traffic Analyzer

Analyze a packet capture and identify:

- Top hosts
- Top protocols
- Top conversations
- DNS activity
- HTTP activity
- Suspicious traffic

---

# Project 02 — Port Scan Investigation

Capture a controlled network scan and investigate:

- Source host
- Target host
- Target ports
- TCP flags
- Scan pattern
- Timeline

Document how the scan appeared in Wireshark.

---

# Project 03 — DNS Investigation

Analyze DNS traffic and identify:

- Requested domains
- Query frequency
- Suspicious domains
- Failed queries
- Unusual patterns

---

# Project 04 — Web Attack Traffic Investigation

Use a controlled vulnerable web application and capture traffic generated during testing.

Investigate:

- HTTP requests
- Parameters
- Headers
- Status codes
- Client IP
- Server IP
- Suspicious requests

---

# Project 05 — Credential Exposure Investigation

Analyze a controlled packet capture containing insecure authentication traffic.

Identify:

- Protocol
- Source
- Destination
- Authentication attempt
- Exposed information
- Security impact

Document the security recommendation.

---

# Project 06 — Malware Traffic Investigation

Using a safe malware-analysis dataset, investigate:

- DNS queries
- Network connections
- Destination IPs
- Repeated connections
- Beaconing behavior
- Suspicious protocols

Extract indicators of compromise.

---

# Project 07 — Full Purple Team Network Investigation

Perform a complete controlled attack-and-detection exercise.

Include:

- Attack activity
- Packet capture
- Wireshark analysis
- Indicators
- Splunk searches
- Timeline
- Detection logic
- MITRE ATT&CK mapping
- Findings
- Defensive recommendations

---

# 🛠️ Tools

- Wireshark
- TShark
- Kali Linux
- Linux
- Windows
- Nmap
- Burp Suite
- Splunk
- Python
- tcpdump
- Virtual Machines
- Security datasets

---

# 📂 Documentation Structure

Each module can contain:

Module-01/

README.md

notes/

screenshots/

pcaps/

filters/

evidence/

Projects can contain:

Project-01/

README.md

pcaps/

filters/

screenshots/

evidence/

findings/

---

# 📈 Skills Checklist

- [ ] Understand packet capture
- [ ] Understand Ethernet
- [ ] Understand ARP
- [ ] Understand IPv4
- [ ] Understand IPv6
- [ ] Understand TCP
- [ ] Understand UDP
- [ ] Analyze TCP handshakes
- [ ] Analyze TCP flags
- [ ] Analyze retransmissions
- [ ] Analyze DNS
- [ ] Analyze HTTP
- [ ] Understand HTTPS/TLS
- [ ] Analyze DHCP
- [ ] Analyze ICMP
- [ ] Use Wireshark display filters
- [ ] Use advanced filters
- [ ] Follow TCP streams
- [ ] Analyze conversations
- [ ] Analyze endpoints
- [ ] Use Wireshark statistics
- [ ] Detect network reconnaissance
- [ ] Investigate brute-force traffic
- [ ] Investigate suspicious HTTP traffic
- [ ] Investigate credential exposure
- [ ] Analyze malware traffic
- [ ] Investigate data exfiltration
- [ ] Extract indicators of compromise
- [ ] Build network timelines
- [ ] Correlate Wireshark with Splunk
- [ ] Map network activity to MITRE ATT&CK
- [ ] Perform a Purple Team network investigation
- [ ] Document packet-analysis investigations

---

# 🟣 Purple Team Integration

Wireshark should not exist separately from the rest of the cybersecurity journey.

It connects the offensive and defensive sides.

## Red Team

Generate network activity.

↓

## Wireshark

Observe and analyze the traffic.

↓

## Blue Team

Detect and investigate the activity.

↓

## Splunk

Correlate network indicators with security logs.

↓

## MITRE ATT&CK

Map the observed behavior.

↓

## Purple Team

Improve the detection and repeat the test.

---

# 🚀 Final Goal

Don't just learn how to capture packets.

Learn how to use network traffic to:

**Observe → Understand → Investigate → Detect → Correlate → Respond → Improve**

The ultimate goal is to understand what attacks look like at the network level and use that visibility to strengthen defensive security.

---

# ⚠️ Legal & Ethical Use

All network monitoring, packet capture, and security testing in this roadmap should be performed only on:

- Systems I own
- My home lab
- Authorized environments
- Intentionally vulnerable systems
- Authorized penetration-testing environments
- Networks where I have explicit permission to monitor

Never capture or inspect network traffic belonging to other people or organizations without authorization.

---

# 👨‍💻 Author

**Dev-Chukwuma**

Backend Developer • Cybersecurity Enthusiast • Django Engineer

GitHub:

https://github.com/Dev-Chukwuma

---

# 🦈 Final Objective

**See the packets.**

**Understand the traffic.**

**Find the attack.**

**Detect the behavior.**

**Investigate the evidence.**

**Improve the defense.**

> **Capture → Filter → Analyze → Investigate → Detect → Document**
