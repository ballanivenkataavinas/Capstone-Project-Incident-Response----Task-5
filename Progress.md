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

# Day 53 - Incident Containment and Firewall Response

Introduction

Incident containment is the process of limiting the impact of a cyberattack after suspicious activity is detected.

The main goals are:
- Stop attacker communication
- Prevent further damage
- Protect critical systems
- Isolate compromised services

Lab Environment

Attacker Machine
- Kali Linux

Target Machine
- Metasploitable2

Tools Used
- iptables
- Netstat
- Wireshark

Step 1 – Check Active Connections

View active network connections:

bash
netstat -tulnp


or

bash
ss -tulnp


Purpose:
- Identify listening services
- Detect suspicious ports
- Monitor active sessions

Step 2 – View Current Firewall Rules

bash
sudo iptables -L


This displays:
- INPUT rules
- OUTPUT rules
- Allowed and blocked traffic


Step 3 – Block Malicious Port

Example: Block Telnet service

bash
sudo iptables -A INPUT -p tcp --dport 23 -j DROP


Purpose:
- Prevent Telnet access
- Reduce attack surface


Step 4 – Allow Secure SSH Access

bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT


Purpose:
- Maintain secure remote administration


Step 5 – Block Specific IP Address

bash
sudo iptables -A INPUT -s <attacker-ip> -j DROP


Example:

bash
sudo iptables -A INPUT -s 1x.1x.x.102 -j DROP


Purpose:
- Prevent malicious host communication

 Step 6 – Disable Unused Services

Check services:

bash
systemctl list-units --type=service


Disable unnecessary service:

bash
sudo systemctl stop apache2


Disable permanently:

bash
sudo systemctl disable apache2


 Step 7 – Verify Firewall Rules

bash
sudo iptables -L


Confirm blocked ports and IPs.


Importance of Incident Containment

Containment helps:
- Stop lateral movement
- Prevent further exploitation
- Limit data exposure
- Reduce attacker persistence


Indicators of Compromise

Common indicators:
- Unusual outbound traffic
- Unknown connections
- Repeated failed logins
- Unexpected open ports


Defensive Security Practices

- Enable firewalls
- Restrict unnecessary ports
- Monitor logs
- Apply security patches
- Disable vulnerable services


Key Concepts Learned

- Incident containment
- Firewall configuration
- Traffic blocking
- Service isolation
- Defensive response techniques



Commands Practiced Today

bash
netstat -tulnp
ss -tulnp
sudo iptables -L
sudo iptables -A INPUT -p tcp --dport 23 -j DROP
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -s <attacker-ip> -j DROP
systemctl list-units --type=service
sudo systemctl stop apache2
sudo systemctl disable apache2

# Day 54 - Incident Eradication and Recovery

Introduction

After detecting and containing an attack, security teams must:
- Remove malicious activity
- Eliminate vulnerabilities
- Restore services safely
- Prevent future compromise

This phase is called:
- Eradication and Recovery

Incident Response Lifecycle

1. Detection  
2. Analysis  
3. Containment  
4. Eradication  
5. Recovery  
6. Reporting  

Today focuses on:
- Eradication
- Recovery

Lab Environment

Attacker Machine
- Kali Linux

Target Machine
- Metasploitable2

Tools Used
- iptables
- systemctl
- netstat
- Linux Logs

Step 1 – Identify Suspicious Services

Check active services:

bash
systemctl list-units --type=service


Purpose:
- Detect unnecessary or suspicious services
- Verify running applications


Step 2 – Stop Vulnerable Services

Example: Stop Telnet service

bash
sudo systemctl stop xinetd


Disable permanently:

bash
sudo systemctl disable xinetd


Purpose:
- Remove insecure services
- Prevent attacker access

Step 3 – Check Open Ports

bash
netstat -tulnp


or

bash
ss -tulnp


Purpose:
- Verify active network ports
- Confirm suspicious ports are closed

Step 4 – Remove Malicious Firewall Rules

View rules:

bash
sudo iptables -L


Flush rules if required:

bash
sudo iptables -F


Purpose:
- Reset incorrect firewall configurations
- Restore proper traffic flow

Step 5 – Apply Security Updates

Update repositories:

bash
sudo apt update


Upgrade packages:

bash
sudo apt upgrade -y


Purpose:
- Patch vulnerabilities
- Improve system security

Step 6 – Restart Essential Services

Restart Apache:

bash
sudo systemctl restart apache2


Restart database:

bash
sudo systemctl restart mariadb


Purpose:
- Restore normal functionality
- Verify service integrity

Step 7 – Monitor Logs

Check authentication logs:

bash
sudo cat /var/log/auth.log


Check Apache logs:

bash
sudo cat /var/log/apache2/access.log


Purpose:
- Investigate attacker actions
- Detect suspicious activity

Recovery Validation

Verify:
- Services running correctly
- No suspicious connections
- Firewall functioning
- Applications accessible

Security Improvements Applied

- Disabled vulnerable services
- Applied patches
- Updated firewall rules
- Reviewed system logs
- Restricted unnecessary access

Importance of Recovery

Recovery ensures:
- Systems return safely online
- Threats are removed
- Services operate securely
- Future attacks are minimized

Key Concepts Learned

- Threat eradication
- Service recovery
- Patch management
- Log analysis
- Secure restoration

Commands Practiced Today

bash
systemctl list-units --type=service
sudo systemctl stop xinetd
sudo systemctl disable xinetd
netstat -tulnp
ss -tulnp
sudo iptables -L
sudo iptables -F
sudo apt update
sudo apt upgrade -y
sudo systemctl restart apache2
sudo systemctl restart mariadb
sudo cat /var/log/auth.log
sudo cat /var/log/apache2/access.log

# Day 55 - Security Monitoring and Log Analysis

Introduction

Security monitoring is the continuous observation of systems, networks, and logs to identify:
- Unauthorized access
- Failed login attempts
- Malware activity
- Suspicious network behavior

Logs are critical sources of evidence during incident investigations.

Importance of Log Analysis

Log analysis helps:
- Detect attacks
- Investigate incidents
- Track attacker activity
- Monitor user behavior
- Improve security posture

Lab Environment

Attacker Machine
- Kali Linux

Target Machine
- Metasploitable2

Tools Used
- Linux Logs
- Wireshark
- Netstat

Types of Important Logs

| Log Type | Purpose |
|---|---|
| Authentication Logs | Login attempts |
| Apache Logs | Web requests |
| System Logs | System events |
| Firewall Logs | Blocked traffic |
| Application Logs | App activities |

Step 1 – Analyze Authentication Logs

View login activity:

bash
sudo cat /var/log/auth.log


Purpose:
- Detect failed logins
- Identify brute-force attacks
- Monitor SSH access

Step 2 – Monitor Apache Access Logs

bash
sudo cat /var/log/apache2/access.log


Purpose:
- Analyze web requests
- Detect suspicious URLs
- Investigate attacker behavior

Step 3 – Analyze Apache Error Logs

bash
sudo cat /var/log/apache2/error.log


Purpose:
- Detect application issues
- Identify malicious requests
- Troubleshoot server problems


Step 4 – Monitor Active Connections

bash
netstat -tulnp


or

bash
ss -tulnp


Purpose:
- Detect suspicious ports
- Identify unknown services
- Monitor active sessions

Step 5 – Real-Time Log Monitoring

Use tail command:

bash
sudo tail -f /var/log/auth.log


Purpose:
- Monitor live authentication activity
- Detect attacks in real time

Indicators of Suspicious Activity

Common indicators:
- Multiple failed logins
- Unknown IP addresses
- Repeated HTTP requests
- Unexpected service activity
- Unusual outbound traffic

Security Monitoring Workflow

1. Collect logs  
2. Analyze events  
3. Detect anomalies  
4. Investigate incidents  
5. Respond to threats  

Importance of Monitoring

Monitoring helps organizations:
- Detect attacks early
- Reduce incident impact
- Improve visibility
- Support forensic investigations


Mitigation Techniques

- Enable centralized logging
- Monitor failed login attempts
- Configure alerts
- Restrict unauthorized access
- Regularly review logs


Key Concepts Learned

- Security monitoring
- Log analysis
- Authentication tracking
- Web log investigation
- Incident detection


Commands Practiced Today

bash
sudo cat /var/log/auth.log
sudo cat /var/log/apache2/access.log
sudo cat /var/log/apache2/error.log
netstat -tulnp
ss -tulnp
sudo tail -f /var/log/auth.log

# Day 56 - Security Hardening and Access Control


Introduction

Security hardening reduces the attack surface of a system by:
- Restricting unauthorized access
- Applying secure configurations
- Limiting user privileges
- Protecting sensitive resources

Access control is one of the most important aspects of cybersecurity defense.


Importance of Access Control

Access control helps:
- Prevent unauthorized access
- Protect sensitive files
- Limit attacker capabilities
- Improve system security

Types of Access Control

| Type | Description |
|---|---|
| Authentication | Verifying user identity |
| Authorization | Granting permissions |
| Accountability | Tracking user actions |

Lab Environment

Attacker Machine
- Kali Linux

Target Machine
- Metasploitable2

Step 1 – View Current Users

bash
cat /etc/passwd


Purpose:
- Display system users
- Identify unnecessary accounts

Step 2 – Create New User

bash
sudo adduser analyst


Purpose:
- Create separate user account
- Improve accountability

Step 3 – Set User Password

bash
sudo passwd analyst


Purpose:
- Configure secure password


Step 4 – Check File Permissions

bash
ls -l


Purpose:
- View read, write, execute permissions


Understanding Linux Permissions

| Permission | Meaning |
|---|---|
| r | Read |
| w | Write |
| x | Execute |

Permission groups:
- Owner
- Group
- Others


Step 5 – Change File Permissions

Example:

bash
chmod 700 confidential.txt


Purpose:
- Restrict unauthorized access


Step 6 – Change File Ownership

bash
sudo chown analyst confidential.txt


Purpose:
- Assign file ownership securely

Step 7 – Disable Root SSH Login

Open SSH configuration:

bash
sudo nano /etc/ssh/sshd_config


Find:

text
PermitRootLogin yes


Change to:

text
PermitRootLogin no


Restart SSH:

bash
sudo systemctl restart ssh


Purpose:
- Prevent direct root access



Step 8 – Lock Unused User Account

bash
sudo passwd -l username


Purpose:
- Disable unnecessary accounts


Security Risks of Poor Access Control

Weak access control can lead to:
- Unauthorized access
- Privilege escalation
- Data theft
- System compromise

Hardening Best Practices

- Use strong passwords
- Limit root access
- Apply least privilege principle
- Restrict file permissions
- Monitor login activity
- Disable unused accounts

Key Concepts Learned

- Access control
- Linux permissions
- User management
- File ownership
- SSH hardening
- System security

Commands Practiced Today

bash
cat /etc/passwd
sudo adduser analyst
sudo passwd analyst
ls -l
chmod 700 confidential.txt
sudo chown analyst confidential.txt
sudo nano /etc/ssh/sshd_config
sudo systemctl restart ssh
sudo passwd -l username
