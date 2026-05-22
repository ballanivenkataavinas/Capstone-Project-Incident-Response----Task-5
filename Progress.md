# Day 49 - Capstone Project Planning & Scope 

Introduction

Before starting any penetration testing or incident response project, proper planning is required to:
- Define targets
- Select tools
- Understand project goals
- Avoid unauthorized testing
- Create proper documentation

Project planning is one of the most important phases in cybersecurity assessments.

Capstone Project Selected
Project Name
Web Application Penetration Testing & Incident Response Simulation

Target Environment

 Vulnerable Systems
- DVWA (Damn Vulnerable Web Application)
- Metasploitable2

Attacker Machine
- Kali Linux

Network Configuration

Virtualization Platform
- VirtualBox

Network Type
- Host-Only Adapter

Purpose:
- Create isolated lab environment
- Prevent external network exposure
- Perform safe testing

Project Objectives

The project focuses on:
- Reconnaissance
- Vulnerability Scanning
- Web Exploitation
- Password Attacks
- Incident Detection
- Traffic Analysis
- System Hardening
- Reporting

Penetration Testing Methodology

Phase 1 – Reconnaissance
Gather target information.

Phase 2 – Scanning
Identify open ports and services.

Phase 3 – Exploitation
Exploit identified vulnerabilities.

Phase 4 – Post-Exploitation
Collect system information and assess impact.

Phase 5 – Reporting
Document findings and mitigations.

Tools Selected

| Tool | Purpose |
|---|---|
| Nmap | Network Scanning |
| Wireshark | Packet Analysis |
| Burp Suite | Web Testing |
| Metasploit | Exploitation |
| Hydra | Password Attacks |
| John the Ripper | Password Cracking |
| iptables | Firewall Configuration |

Project Scope

Included
- Controlled exploitation
- Vulnerability scanning
- Incident simulation
- Defensive security controls

Excluded
- Real-world targets
- Internet-facing systems
- Unauthorized testing

Timeline Planning

| Phase | Activity |
|---|---|
| Planning | Define scope and tools |
| Scanning | Recon and enumeration |
| Exploitation | Controlled attacks |
| Incident Response | Detection and mitigation |
| Reporting | Documentation |

Deliverables Planned

- Security Assessment Report
- Screenshots and Evidence
- GitHub Documentation
- Incident Response Notes
- Final Demonstration Video

Risk Considerations

Potential risks:
- Service crashes
- Resource exhaustion
- Misconfiguration

Mitigation:
- Use isolated lab
- Take VM snapshots
- Monitor services

Key Concepts Learned

- Project planning
- Scope definition
- Penetration testing workflow
- Tool selection
- Risk management

Commands Practiced Today

bash
ifconfig
ping <target-ip>
nmap -sV <target-ip>

# Day 50 - Network Reconnaissance and Vulnerability Assessment

Introduction

Reconnaissance and scanning are the first technical phases of penetration testing. These phases help identify:
- Active hosts
- Open ports
- Running services
- Vulnerabilities
- Attack surface

Lab Environment

Attacker Machine
- Kali Linux

Target Machines
- Metasploitable2
- DVWA

Step 1 – Verify Network Connectivity

Check attacker IP:

bash
ifconfig


Ping target system:

bash
ping <target-ip>


Purpose:
- Verify target is reachable
- Confirm network communication

Step 2 – Basic Port Scanning

Perform service scan:

bash
nmap -sV <target-ip>


This scan identifies:
- Open ports
- Running services
- Service versions

Step 3 – Aggressive Scan

bash
sudo nmap -A <target-ip>


Aggressive scan performs:
- OS detection
- Service enumeration
- Script scanning
- Traceroute

Step 4 – Vulnerability Scanning

Run vulnerability detection scripts:

bash
nmap --script vuln <target-ip>


Purpose:
- Detect known vulnerabilities
- Identify weak services
- Find misconfigurations

Step 5 – UDP Scan

bash
sudo nmap -sU <target-ip>


Checks UDP services such as:
- DNS
- SNMP
- DHCP

Step 6 – Save Scan Results

Save output to file:

bash
nmap -sV <target-ip> -oN scan_report.txt


Purpose:
- Documentation
- Evidence collection
- Reporting

Services Identified

Common vulnerable services:
- FTP
- SSH
- Telnet
- HTTP
- SMB

Security Risks Observed

- Outdated services
- Open unnecessary ports
- Weak configurations
- Exposed vulnerable applications

Importance of Reconnaissance

Recon helps attackers:
- Map the target
- Identify entry points
- Plan exploitation strategy

It also helps defenders:
- Understand exposure
- Detect weaknesses
- Improve security posture

Mitigation Techniques

- Disable unused services
- Close unnecessary ports
- Apply security patches
- Restrict network access
- Monitor suspicious traffic

Key Concepts Learned

- Host discovery
- Port scanning
- Service enumeration
- Vulnerability assessment
- Network reconnaissance

Commands Practiced Today

bash
ifconfig
ping <target-ip>
nmap -sV <target-ip>
sudo nmap -A <target-ip>
nmap --script vuln <target-ip>
sudo nmap -sU <target-ip>
nmap -sV <target-ip> -oN scan_report.txt

Day 51 - Web Application Security Assessment

Introduction

Web application security testing helps identify vulnerabilities that attackers can exploit to:
- Steal sensitive data
- Bypass authentication
- Execute malicious scripts
- Gain unauthorized access

Lab Environment

Attacker Machine
- Kali Linux

Target Application
- DVWA (Damn Vulnerable Web Application)

Tools Used
- Burp Suite
- Browser
- DVWA

Step 1 – Start DVWA Services

Start Apache:

bash
sudo systemctl start apache2


Start MariaDB:

bash
sudo systemctl start mariadb


Step 2 – Access DVWA

Open browser:

text
http://127.0.0.1/dvwa


Login credentials:

text
Username: admin
Password: password

Step 3 – Configure DVWA Security Level

Go to:
- DVWA Security

Set:
- Security Level = Low

Purpose:
- Demonstrate vulnerabilities easily

Step 4 – SQL Injection Testing

Navigate to:
- SQL Injection section

Test payload:

sql
' OR '1'='1


Purpose:
- Bypass SQL query validation
- Extract database information

Step 5 – Cross-Site Scripting (XSS)

Navigate to:
- XSS (Stored)

Payload:

html
<script>alert('XSS')</script>


Result:
- JavaScript executes inside browser

Step 6 – Reflected XSS

Navigate to:
- XSS (Reflected)

Inject:

html
<script>alert('Reflected')</script>


Purpose:
- Demonstrate user-input execution

Step 7 – Request Interception with Burp Suite

Start Burp Suite:

bash
burpsuite


Enable:
- Proxy → Intercept ON

Capture HTTP requests:
- Login requests
- Form submissions
- Parameters

Step 8 – Analyze Security Risks

Observed risks:
- Input validation failure
- Unsanitized user input
- Weak authentication
- Session exposure

Common OWASP Risks Identified

- SQL Injection
- Cross-Site Scripting
- Broken Authentication
- Security Misconfiguration

Mitigation Techniques

- Prepared statements
- Input validation
- Output encoding
- Content Security Policy (CSP)
- Strong authentication

Key Concepts Learned

- Web vulnerability testing
- SQL Injection basics
- Stored and Reflected XSS
- Request interception
- Web security risks

Commands Practiced Today

bash
sudo systemctl start apache2
sudo systemctl start mariadb
burpsuite

# Day 52 - Incident Detection and Traffic Analysis


Introduction

Incident detection is the process of identifying suspicious or unauthorized activity within a network or system.

Traffic analysis helps security analysts:
- Detect attacks
- Investigate incidents
- Monitor communications
- Identify malicious packets

Lab Environment

Attacker Machine
- Kali Linux

Target Machine
- Metasploitable2

Tool Used
- Wireshark

Step 1 – Start Wireshark

Open terminal:

bash
wireshark


Or open from applications menu.

Step 2 – Select Network Interface

Choose active interface:
- eth0
- enp0s3

Start packet capture.

Step 3 – Generate Network Traffic

Ping target machine:

bash
ping <target-ip>


Open DVWA in browser:

text
http://<target-ip>/dvwa


Purpose:
- Generate HTTP and ICMP traffic

Step 4 – Analyze ICMP Traffic

Wireshark filter:

text
icmp


Observe:
- Echo requests
- Echo replies
- Source and destination IPs

Step 5 – Analyze HTTP Traffic

Filter:

text
http


Observe:
- GET requests
- POST requests
- URLs
- User-Agent headers

Step 6 – Analyze DNS Traffic

Filter:

text
dns


Purpose:
- Identify domain lookups
- Monitor DNS activity

Step 7 – Detect Suspicious Activity

Indicators observed:
- Repeated requests
- Unusual traffic spikes
- Unauthorized connections
- Large packet volume

Step 8 – Capture Credentials from FTP

Filter:

text
ftp


Observe:
- Plaintext usernames
- Plaintext passwords

This demonstrates why unencrypted protocols are dangerous.

Step 9 – Export Packet Capture

Save capture file:
- File → Save As

Format:
- .pcap

Purpose:
- Incident evidence
- Future analysis
- Reporting

Common Attack Indicators

- Port scanning
- SYN floods
- Brute-force attempts
- Unusual outbound traffic

Importance of Traffic Analysis

Traffic analysis helps:
- Detect intrusions
- Investigate incidents
- Monitor attacks
- Improve network visibility

Mitigation Techniques

- Use encrypted protocols
- Monitor traffic continuously
- Deploy IDS/IPS systems
- Configure firewall rules
- Analyze suspicious logs

Key Concepts Learned

- Packet capture
- Protocol analysis
- Traffic filtering
- Incident detection
- Suspicious activity analysis

Commands Practiced Today

bash
wireshark
ping <target-ip>

Wireshark Filters Practiced

text
icmp
http
dns
ftp

