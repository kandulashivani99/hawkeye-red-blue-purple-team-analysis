# hawkeye-red-blue-purple-team-analysis
# SOC

## Overview
This repository contains a complete analysis of the HawkEye Keylogger – Reborn v9 malware challenge from CyberDefenders.

## Objectives
- Analyze malicious PCAP traffic
- Investigate malware behavior
- Identify Indicators of Compromise (IOCs)
- Simulate Red Team attack methodology
- Develop Blue Team detection strategies
- Create Purple Team collaboration findings

## Skills Demonstrated
- Wireshark Analysis
- Malware Traffic Analysis
- Threat Hunting
- IOC Extraction
- SMTP Analysis
- Incident Response
- MITRE ATT&CK Mapping
- Detection Engineering

## Tools Used
- Wireshark
- CyberChef
- VirusTotal
- AbuseIPDB
- WHOIS Lookup

## Reports Included
- Red Team Report
- Blue Team Report
- Purple Team Handover Report

# RED TEAM REPORT
## HawkEye Malware Attack Simulation Report

The Red Team is to simulate a realistic malware attack using HawkEye Keylogger techniques. 
This report demonstrates how an attacker compromise’s target system, steals credentials, and 
exfiltrates sensitive information while avoiding detection.

Red Team Phases
1.	Reconnaissance 
2.	Initial Access 
3.	Execution 
4.	Persistence 
5.	Privilege Escalation 
6.	Credential Access 
7.	Discovery 
8.	Lateral Movement 
9.	Collection 
10.	Command and Control (C2) 
11.	Exfiltration 
12.	Impact

1.	Reconnaissance Phase
The Target Information Gathering where an attacker performs reconnaissance to identify the
•	Operating systems in use
•	Email services
•	Platforms
•	Potential victims etc

Observation:
•	Hostname: BEIJING-5CD1-PC
•	User: roman.mcguire
•	Operating System: Windows 7 x64

2.	Initial Access
The attacker delivers malware through a downloaded malicious executable file tkraw_Protected99.exe

Potential attack vectors include:
•	Phishing email attachment
•	Fake invoice download
•	Malicious website
The attacker tricks the victim into downloading and executing the malware.

Observation:
•	Malicious domain: proforma-invoices.com

3.	Execution Phase
After execution, HawkEye Keylogger becomes active on the victim system.

Actions Performed
•	Creates persistence
•	Starts keylogging
•	Accesses browser credential databases
•	Reads Outlook credentials
•	Collects system information

Indicators
•	Suspicious executable launched
•	Unauthorized access to browser storage
•	Credential harvesting activity

4. Credential Harvesting

Credentials Stolen
AOL Credentials
•	Username: roman.mcguire914@aol.com
•	Password: P@ssw0rd$
Bank of America Credentials
•	Username: roman.mcguire
•	Password: P@ssw0rd$
Outlook Credentials
•	Email: roman.mcguire@pizzajukebox.com
•	POP3 Server: pop.pizzajukebox.com
<img width="559" height="636" alt="image" src="https://github.com/user-attachments/assets/d02ed95e-ac52-4ef7-ac4b-524da3e296d8" />

Browser Targets
•	Internet Explorer
•	Google Chrome
Techniques Used
•	Browser credential dumping
•	Keylogging
•	Email credential extraction

5. Command and Control / Exfiltration
The malware exfiltrates stolen information through SMTP.

SMTP Server Details
•	IP Address: 23.229.162.69
•	Hosting Provider: GoDaddy
Exfiltrated Data
•	Banking credentials
•	Email passwords
•	Browser credentials
•	Victim system information
Attack Objectives
•	Financial theft
•	Account compromise
•	Identity theft
•	Persistence for future attacks

6. Red Team Operations

Attack Success Factors
•	Victim executed malware manually.
•	HTTP traffic was unencrypted.
•	Endpoint protection was absent or ineffective.
•	Credentials were stored in browsers.

Stealth Techniques
•	Legitimate SMTP communication
•	Common file naming
•	Credential theft without privilege escalation

7. Red Team Recommendations

Improvements for Attack Simulation
•	Add persistence mechanisms
•	Use HTTPS delivery instead of HTTP
•	Encrypt exfiltrated payloads
•	Implement sandbox evasion

# BLUE TEAM REPORT
## HawkEye Malware Detection and Incident Response Report

The Blue Team investigation focuses on detecting malicious activity, analyzing the compromise, identifying indicators of compromise (IOCs), and recommending defensive controls.

1.	Detection

Initial Indicators
The investigation identified suspicious:
•	HTTP downloads
•	SMTP traffic
•	Credential exfiltration
•	Malware execution patterns
Detection Sources
•	Wireshark PCAP analysis
•	HTTP object extraction
•	SMTP inspection
•	IOC correlation

2. Malware Analysis

Identified Malware
•	HawkEye Keylogger – Reborn v9
Malicious File
tkraw_Protected99.exe
<img width="975" height="426" alt="image" src="https://github.com/user-attachments/assets/062fef29-6d89-4e21-922e-85ace2878e45" />

Malware Capabilities
•	Keylogging
•	Credential theft
•	Email credential theft
•	SMTP exfiltration

4. Network Analysis

HTTP Traffic Findings
The victim downloaded the malware from:
proforma-invoices.com
<img width="975" height="527" alt="image" src="https://github.com/user-attachments/assets/12f47ddd-bde4-4433-aeeb-8c0a83228c83" />

Observations
•	Executable transferred over HTTP
•	Suspicious executable file observed
•	User-Agent identified victim environment indicating Windows 7 x64 system

6.	SMTP Traffic Analysis

Exfiltration Detection
SMTP traffic revealed outbound transmission of:
•	Password logs
•	Victim system details
•	Browser credentials
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/8c1ba28b-f9bf-413c-8558-4c93d00d1b21" />

SMTP Indicators
•	Destination IP: 23.229.162.69
•	Suspicious outbound email activity
•	Unauthorized credential transmission

7. Compromised Credentials

Banking Credentials
•	Username: roman.mcguire
•	Password: P@ssw0rd$
Email Credentials
•	roman.mcguire914@aol.com
•	roman.mcguire@pizzajukebox.com
<img width="559" height="636" alt="image" src="https://github.com/user-attachments/assets/4c6d4aa3-a86d-4cfb-9211-44f258e8b904" />

Risk Assessment
The compromise may lead to:
•	Financial fraud
•	Identity theft
•	Unauthorized email access
•	Network compromise

8. Indicators of Compromise (IOCs)

File IOC
•	tkraw_Protected99.exe
Domain IOC
•	proforma-invoices.com
IP IOC
•	23.229.162.69
Malware Family
•	HawkEye Keylogger – Reborn v9

9. Blue Team (Defensive Actions)

Immediate Response
•	Isolate infected host
•	Block malicious IPs/domains
•	Reset compromised credentials
•	Scan systems for persistence
•	Investigate lateral movement

Recommended Security Controls

•	Endpoint Security
•	Email Security
•	Network Security
•	Security awareness training
•	Phishing simulations
•	Password management training

Blue Team Lessons Learned

•	Users storing passwords in browsers are high-risk targets.
•	SMTP traffic monitoring is critical.
•	Unencrypted HTTP downloads increase exposure.
•	Credential theft malware can operate quietly.

# PURPLE TEAM REPORT
## HawkEye Purple Team Handover Report

The Purple Team combines Red Team offensive techniques with Blue Team defensive analysis to improve detection, response, and organizational resilience.
The HawkEye malware attack successfully compromised a Windows 7 workstation through a malicious executable download. 
The malware harvested browser, banking, and email credentials before exfiltrating the information using SMTP communication.

The purple team demonstrated weaknesses in:
•	User awareness
•	Endpoint monitoring
•	HTTP traffic inspection
•	Credential storage practices

Blue Team analysis successfully identified:
•	Malware download activity
•	Credential theft indicators
•	SMTP exfiltration
•	Compromised accounts

Attack Chain Overview

Initial Access
•	Victim downloaded malicious executable.
•	Malware executed successfully.
Execution
•	HawkEye Keylogger initiated credential harvesting.
Credential Access
•	Browser credentials extracted.
•	Outlook credentials stolen.
•	Banking credentials harvested.
Exfiltration
•	Data transmitted through SMTP

Purple Team Collaboration Findings

Red Team Insights
•	Users are vulnerable to socially engineered downloads.
•	Browser-stored credentials are easy targets.
•	SMTP exfiltration often bypasses detection.

Blue Team Insights
•	HTTP executable downloads require stricter monitoring.
•	SMTP traffic should be inspected for anomalies.
•	Endpoint telemetry is essential.

Improvements
New Detection Opportunities

Endpoint Detection
•	Detect browser credential database access.
•	Alert on keylogging behavior.

Network Detection
•	Detect outbound SMTP anomalies.
•	Monitor suspicious HTTP executable downloads.

SIEM Correlation
•	Correlate executable downloads with SMTP traffic.
•	Identify credential theft patterns.

Technical Recommendations
•	Deploy EDR/XDR solutions.
•	Enforce MFA on banking/email accounts.
•	Block executable downloads from unknown domains.
•	Encrypt web traffic.
•	Implement DNS filtering.

# Final IOC Summary

IOC Type	                        Value
Malware	                  HawkEye Reborn v9
Executable	              tkraw_Protected99.exe
Domain                  	proforma-invoices.com
IP Address	              23.229.162.69
Victim                    Host	BEIJING-5CD1-PC
User	                    roman.mcguire

Conclusion

The HawkEye investigation demonstrates a complete malware infection lifecycle involving delivery, execution, credential theft, and exfiltration. The exercise highlights the importance of:
•	Proactive monitoring
•	Threat hunting
•	User awareness
•	SIEM correlation
•	Endpoint visibility

The Purple Team collaboration successfully identified detection gaps and improved both offensive understanding and defensive readiness.

I created the complete set of:
•	Red Team report 
•	Blue Team report 
•	Purple Team handover report 

for solved HawkEye CyberDefenders lab, including:
•	attack flow 
•	malware analysis 
•	IOC analysis
•	Detection Recommandations.

## Malware Information
- Malware Family: HawkEye Keylogger – Reborn v9
- Malware File: tkraw_Protected99.exe

## Key Findings
- Credential theft
- SMTP exfiltration
- Browser password harvesting
- Banking credential compromise
