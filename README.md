# CSIRT: PathCode
This project investigates Capital One's 2019 data breach. It also uses Splunk to detect and explore a malware attack, and then uses Catalyst to document the response to the attack.

## Overview
The goal of this project was to simulate real-world incident response by:
- Investigating a malware incident using Splunk logs
- Creating and managing a case in Catalyst
- Researching IOCs like hashes and IPs using VirusTotal
- Documenting tasks, artifacts, and TTPs
- Writing up Lessons Learned and applying the NIST Cybersecurity Framework

## Tools Used
- Splunk
- Catalyst
- VirusTotal

## Screenshots
#### Splunk Log Analysis:
<img src="https://github.com/user-attachments/assets/d6d42034-b3d8-43c9-ab31-f924a69deb84" width="600"/>

---

#### VirusTotal report for EvilScript.exe's file hash:
<img src="https://github.com/user-attachments/assets/fd869203-ae4f-46f7-b5a0-af8d7ea75e9b" width="600"/>

---

#### PathCode ticket in Catalyst:
<img src="https://github.com/user-attachments/assets/2898a2bb-b057-4201-82bd-c79e373f525b" width="600"/>

<img src="https://github.com/user-attachments/assets/5c8662f6-de12-4a86-a80d-5844f8ff3131" width="600"/>

---

## Findings
The investigation revealed that `EvilScript.exe` was uploaded using a compromised internal account (`ABurke`). Logs tied the upload to IP `192.168.1.10`, and the file hash was confirmed as malware via VirusTotal. The user account was likely compromised due to weak authentication controls.

## Lessons Learned
- **MFA** should be mandatory for internal accounts like ABurke
- Improve internal upload monitoring and trigger alerts for suspicious activity
- Response time would benefit from automated playbooks or SOAR integration in a real SOC environment

## Real-World Breach Analysis (Capital One)
#### Capital One 2019 Breach Ticket in Catalyst
<img src="https://github.com/user-attachments/assets/90655232-9cf7-4715-86c6-c769dc4b130b" width="600"/>

Using the **NIST Cybersecurity Framework**, I broke down how the Capital One breach could have been prevented:

1. **Identify:** Missed AWS WAF misconfigurations  
2. **Protect:** Lack of least privilege on IAM roles; open access to metadata API  
3. **Detect:** No alerts for SSRF or unusual S3 access  
4. **Respond:** Response occurred post-breach; needed predefined cloud abuse playbooks  
5. **Recover:** Public comms and IAM revalidation were reactive but could be more robust

## Reflections
This lab showed me how tools like **Catalyst** help centralize documentation, making it easier to track progress and stay organized during an incident. Adding real IOCs, verifying them with VirusTotal, and writing actionable Lessons Learned felt like an intro to real SOC workflows.

---

