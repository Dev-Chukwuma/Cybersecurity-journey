# 🕷️ Burp Suite Learning Roadmap

A hands-on journey to learn **Burp Suite**, understand HTTP/HTTPS traffic, intercept and manipulate web requests, test web applications, investigate vulnerabilities, and develop practical web application security skills.

> **Learn → Intercept → Analyze → Test → Hunt → Document**

---

## 🎯 Goal

The goal of this roadmap is to build practical Burp Suite and web application security skills through hands-on labs, vulnerability testing, API security testing, web security investigations, and practical projects.

By the end, I should be able to:

- Understand HTTP and HTTPS
- Understand how web applications communicate
- Configure Burp Suite
- Intercept web traffic
- Analyze HTTP requests and responses
- Manipulate web requests
- Use Burp Repeater
- Use Burp Intruder
- Use Burp Decoder
- Use Burp Comparer
- Work with Burp extensions
- Test authentication
- Test authorization
- Identify IDOR/BOLA vulnerabilities
- Test common web vulnerabilities
- Analyze APIs
- Test JWT authentication
- Analyze GraphQL applications
- Test WebSockets
- Build web security findings
- Document vulnerabilities
- Write professional security reports

---

# 🗺️ Learning Roadmap

## 🟢 Phase 1 — Burp Suite Fundamentals

### Module 01 — Introduction to Burp Suite

- What is Burp Suite?
- What is web application security?
- How Burp Suite works
- Proxy-based security testing
- Burp Suite Community Edition
- Burp Suite Professional
- Burp Suite interface
- Understanding the Burp workflow

### Module 02 — Web Application Fundamentals

- HTTP
- HTTPS
- Requests
- Responses
- HTTP methods
- GET
- POST
- PUT
- DELETE
- Headers
- Status codes
- Parameters
- Cookies
- Sessions

### Module 03 — Burp Proxy

Learn how to:

- Intercept requests
- Forward requests
- Drop requests
- Modify requests
- Inspect responses
- View HTTP history
- Configure proxy settings

### Module 04 — Browser & Burp Configuration

Learn:

- Browser proxy configuration
- Burp embedded browser
- Burp CA certificate
- HTTPS interception
- Certificate errors
- Proxy troubleshooting
- Target scope

### Module 05 — Target & Site Map

Learn:

- Target tab
- Site map
- Target scope
- HTTP history
- Endpoints
- Parameters
- Application structure
- Crawling concepts

---

# 🟡 Phase 2 — Request Manipulation

### Module 06 — Burp Repeater

Learn:

- Sending requests manually
- Modifying parameters
- Modifying headers
- Changing HTTP methods
- Testing responses
- Comparing response behavior

Request  
↓  
Modify  
↓  
Send  
↓  
Analyze  
↓  
Repeat

### Module 07 — Burp Intruder

Learn:

- Intruder fundamentals
- Positions
- Payloads
- Attack types
- Sniper
- Battering Ram
- Pitchfork
- Cluster Bomb
- Response analysis

### Module 08 — Burp Decoder

Learn:

- URL encoding
- URL decoding
- Base64
- HTML encoding
- Hexadecimal
- Unicode
- Encoding vs encryption
- Encoding vs hashing

### Module 09 — Burp Comparer

Learn:

- Comparing requests
- Comparing responses
- Identifying differences
- Authentication testing
- Response analysis
- Finding subtle changes

### Module 10 — Burp Extensions

Learn:

- Burp Extender
- BApps
- Extensions
- Extension configuration
- Extension security
- Useful Burp extensions
- Introduction to custom extensions

---

# 🟠 Phase 3 — Web Security Testing

### Module 11 — Authentication Testing

Analyze:

- Login functionality
- Authentication requests
- Authentication parameters
- Password reset
- Account lockout
- Authentication controls
- Authentication weaknesses

Login Request  
↓  
Intercept  
↓  
Analyze  
↓  
Test  
↓  
Document

### Module 12 — Session Management

Learn:

- Cookies
- Session IDs
- Session tokens
- Session expiration
- Logout functionality
- Session fixation
- Session manipulation

### Module 13 — Access Control

Learn:

- Authentication vs authorization
- Horizontal privilege escalation
- Vertical privilege escalation
- IDOR
- BOLA
- Role-based access
- Authorization testing

User A  
↓  
Request  
↓  
Modify Identifier  
↓  
Test Access  
↓  
Analyze Response

### Module 14 — SQL Injection

Learn:

- SQL injection fundamentals
- Injection points
- Parameter testing
- Error-based behavior
- Boolean-based testing
- Time-based concepts
- Response analysis

Input  
↓  
SQL Query  
↓  
Unexpected Behavior  
↓  
Analyze  
↓  
Validate

### Module 15 — Cross-Site Scripting

Learn:

- Reflected XSS
- Stored XSS
- DOM XSS
- Input reflection
- Context analysis
- Output encoding
- XSS validation

### Module 16 — Command & Code Injection

Learn:

- Command injection
- Server-side injection
- Code injection concepts
- Input validation
- Injection points
- Detection techniques
- Safe validation

### Module 17 — File Upload & Path Traversal

Learn:

- File upload functionality
- File extensions
- MIME types
- Filename validation
- Path traversal
- Local file inclusion concepts
- File handling weaknesses

---

# 🔴 Phase 4 — Advanced Web Testing

### Module 18 — SSRF

Learn:

- What is SSRF?
- Server-side requests
- Internal services
- URL validation
- SSRF detection
- Blind SSRF concepts
- SSRF impact

Application  
↓  
Server  
↓  
Internal Request  
↓  
Unexpected Resource  
↓  
SSRF

### Module 19 — XXE

Learn:

- XML fundamentals
- XML parsers
- External entities
- XXE detection
- File disclosure concepts
- SSRF through XXE

### Module 20 — API Security Testing

Learn:

- REST APIs
- JSON
- API endpoints
- API authentication
- API parameters
- HTTP methods
- API authorization
- BOLA
- IDOR

API Request  
↓  
Intercept  
↓  
Modify  
↓  
Send  
↓  
Analyze  
↓  
Document

### Module 21 — JWT Testing

Learn:

- What is JWT?
- JWT structure
- Header
- Payload
- Signature
- JWT decoding
- Claims
- Token validation
- Algorithm concepts
- Token manipulation

### Module 22 — GraphQL Security

Learn:

- What is GraphQL?
- Queries
- Mutations
- GraphQL endpoints
- Introspection
- Authorization
- GraphQL injection concepts
- GraphQL request analysis

### Module 23 — WebSockets

Learn:

- WebSocket fundamentals
- WebSocket handshake
- WebSocket messages
- Message interception
- Message manipulation
- Authentication
- Authorization

---

# 🟣 Phase 5 — Advanced Burp Testing

### Module 24 — Automated Scanning Concepts

Learn:

- Passive scanning
- Active scanning
- Automated vulnerability detection
- Scanner limitations
- False positives
- Manual verification
- Vulnerability validation

Scanner Finding  
↓  
Manual Testing  
↓  
Validation  
↓  
Evidence  
↓  
Report

### Module 25 — Advanced Intruder

Learn:

- Custom payloads
- Payload processing
- Payload encoding
- Response analysis
- Attack optimization
- Rate limiting
- Controlled request generation

### Module 26 — Burp + Security Tools

Learn how Burp works alongside:

- Nmap
- Gobuster
- ffuf
- Nuclei
- Wireshark
- Python
- Kali Linux

Recon  
↓  
Enumeration  
↓  
Burp  
↓  
Testing  
↓  
Validation  
↓  
Documentation

### Module 27 — Vulnerability Reporting

Learn how to document:

- Vulnerability title
- Description
- Affected endpoint
- HTTP request
- HTTP response
- Evidence
- Impact
- Severity
- Reproduction steps
- Remediation

Finding  
↓  
Evidence  
↓  
Impact  
↓  
Remediation  
↓  
Report

---

# ⚫ Phase 6 — Web Security Hunting

### Module 28 — Bug Bounty Methodology

Learn:

- Reconnaissance
- Attack surface discovery
- Endpoint discovery
- Parameter discovery
- Authentication testing
- Authorization testing
- Vulnerability validation
- Evidence collection
- Vulnerability reporting

Recon  
↓  
Attack Surface  
↓  
Testing  
↓  
Validation  
↓  
Report

Only test systems where testing is explicitly authorized.

### Module 29 — Advanced Web Vulnerability Hunting

Combine everything learned so far:

- Authentication vulnerabilities
- Authorization vulnerabilities
- IDOR
- BOLA
- XSS
- SQL injection
- SSRF
- XXE
- File upload vulnerabilities
- Path traversal
- API vulnerabilities
- JWT vulnerabilities
- GraphQL vulnerabilities
- WebSocket vulnerabilities
- Business logic vulnerabilities

Target  
↓  
Recon  
↓  
Map Application  
↓  
Identify Attack Surface  
↓  
Test  
↓  
Validate  
↓  
Document

---

# 🏁 Phase 7 — Practical Capstone

### Module 30 — Full Web Application Security Assessment

Perform a complete security assessment against an authorized laboratory application.

Assessment workflow:

Target  
↓  
Scope  
↓  
Reconnaissance  
↓  
Proxy  
↓  
Site Map  
↓  
Request Analysis  
↓  
Repeater  
↓  
Intruder  
↓  
Vulnerability Testing  
↓  
Validation  
↓  
Evidence  
↓  
Reporting

The assessment should include:

- Application mapping
- Endpoint discovery
- Parameter analysis
- Authentication testing
- Session testing
- Authorization testing
- Input validation testing
- API testing
- Common vulnerability testing
- Evidence collection
- Finding validation
- Vulnerability documentation
- Remediation recommendations

---

# 🧪 Recommended Practice Environments

Practice only on systems I own, intentionally vulnerable applications, authorized labs, or security programs that explicitly permit testing.

Recommended environments:

- PortSwigger Web Security Academy
- OWASP Juice Shop
- DVWA
- OWASP WebGoat
- Local Django applications
- Local intentionally vulnerable applications
- Authorized bug bounty programs

---

# 🧰 Tools

- Burp Suite
- Kali Linux
- Firefox
- Burp Browser
- Nmap
- Gobuster
- ffuf
- Nuclei
- Wireshark
- Python
- Git
- GitHub

---

# 📂 Documentation Structure

Each module can contain:

Module-01/  
├── README.md  
├── notes/  
└── screenshots/

Projects can contain:

Project/  
├── README.md  
├── evidence/  
├── screenshots/  
└── reports/

---

# 📈 Skills Checklist

- [ ] Understand HTTP
- [ ] Understand HTTPS
- [ ] Understand web requests
- [ ] Understand web responses
- [ ] Configure Burp Suite
- [ ] Configure browser proxy
- [ ] Intercept HTTP traffic
- [ ] Analyze HTTP requests
- [ ] Analyze HTTP responses
- [ ] Use Burp Proxy
- [ ] Use Burp Repeater
- [ ] Use Burp Intruder
- [ ] Use Burp Decoder
- [ ] Use Burp Comparer
- [ ] Use Burp Extensions
- [ ] Test authentication
- [ ] Test session management
- [ ] Test authorization
- [ ] Identify IDOR/BOLA
- [ ] Test SQL injection
- [ ] Test XSS
- [ ] Test command injection
- [ ] Test file upload functionality
- [ ] Test path traversal
- [ ] Test SSRF
- [ ] Test XXE
- [ ] Test APIs
- [ ] Analyze JWT
- [ ] Test GraphQL
- [ ] Analyze WebSockets
- [ ] Validate automated findings
- [ ] Perform web security investigations
- [ ] Write vulnerability reports
- [ ] Complete a web security assessment

---

# 🚀 Final Goal

Don't just learn how to **use Burp Suite**.

Learn how to use Burp Suite to:

**Intercept → Analyze → Test → Validate → Explain → Document**

web application security vulnerabilities.

---

# ⚠️ Legal & Ethical Use

Burp Suite is a professional security testing tool.

All testing performed as part of this repository should be conducted against:

- Systems I own
- Local laboratory environments
- Intentionally vulnerable applications
- Authorized penetration-testing environments
- Bug bounty programs where testing is explicitly permitted

Unauthorized testing can cause harm and may violate laws or terms of service.

---

# 📚 Resources

- PortSwigger Web Security Academy
- Burp Suite Documentation
- OWASP Web Security Testing Guide
- OWASP Top 10
- OWASP API Security Top 10
- OWASP Juice Shop
- DVWA
- OWASP WebGoat

---

# 👨‍💻 Author

**Dev-Chukwuma**

Backend Developer • Purple teamer in training • Django Engineer

GitHub: https://github.com/Dev-Chukwuma

---

# 🚀 Next Chapter

**Web Application & Penetration Testing**
