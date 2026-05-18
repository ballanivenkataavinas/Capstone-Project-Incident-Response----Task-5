# Task 5 - Capstone Project & Incident Response

Objective
Perform a complete cybersecurity assessment and incident response simulation in a controlled lab environment using offensive and defensive security techniques.


Lab Environment

| Component | Description |
|---|---|
| Attacker Machine | Kali Linux |
| Target Machines | Metasploitable2, DVWA |
| Virtualization | VirtualBox |
| Network | Host-Only Adapter |

Topics Covered

- Reconnaissance & Scanning
- Vulnerability Assessment
- SQL Injection & XSS
- Exploitation with Metasploit
- Password Attacks
- Incident Detection & Response
- Firewall & System Hardening
- Security Reporting

Tools Used

- Nmap
- Wireshark
- Burp Suite
- Metasploit Framework
- Hydra
- John the Ripper
- DVWA
- iptables

Sample Commands

Scanning

bash
nmap -sV <target-ip>


Exploitation

bash
msfconsole

Password Attack

bash
hydra -l msfadmin -P rockyou.txt ssh://<target-ip>

Incident Response Workflow

1. Detection  
2. Analysis  
3. Containment  
4. Eradication  
5. Recovery  
6. Reporting  

Deliverables

- Capstone Security Report
- GitHub Repository
- Screenshots & Notes
- 12-Minute Demo Video
