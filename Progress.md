# Day 49 - Capstone Project Planning & Scope Definition

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

