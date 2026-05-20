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
