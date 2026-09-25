# Cybersecurity-Capstone-Project

# Phishing Attack & Employee Account Compromise Investigation

## Cybersecurity Incident Response Case Study

### Overview

This project documents the investigation and response to a simulated phishing attack against **Dansoman Community Bank**, a fictional community bank created for a cybersecurity capstone project.

The incident began when a Finance Department employee clicked a malicious link in a spoofed IT-support email. The compromised credentials were subsequently used to access internal systems, including the Core Banking Server.

The investigation reconstructed the attack by correlating firewall, authentication, and endpoint logs.

> **Note:** Dansoman Community Bank is a fictional organization created for this project. All sensitive information and infrastructure details are used for educational purposes.

---

## Incident Summary

| Category              | Details                                       |
| --------------------- | --------------------------------------------- |
| Incident Type         | Phishing / Account Compromise                 |
| Initial Access        | Spearphishing Link                            |
| Affected User         | Finance Department employee                   |
| Initial Access Time   | 09:12                                         |
| Core Banking Access   | 09:24:51                                      |
| Primary Attack Vector | Phishing                                      |
| Persistence           | Scheduled Task                                |
| Command & Control     | External network connection                   |
| Key Security Gap      | Lack of MFA                                   |
| Investigation Focus   | Timeline reconstruction and incident response |

---

## Objectives

The investigation aimed to:

* Reconstruct the attack timeline.
* Identify the initial attack vector.
* Analyze authentication and network activity.
* Identify indicators of compromise.
* Map observed activity to MITRE ATT&CK techniques.
* Assess the impact of the compromise.
* Document containment, eradication, and recovery actions.
* Recommend controls to prevent similar incidents.

---

## Attack Timeline

The investigation correlated multiple log sources to reconstruct the following sequence:

| Time        | Event                                               | MITRE ATT&CK |
| ----------- | --------------------------------------------------- | ------------ |
| 09:12       | Employee receives spoofed IT-support email          | T1566.002    |
| 09:13       | Employee clicks malicious link                      | T1204.001    |
| 09:14       | Failed external login attempt                       | T1078        |
| 09:14:47    | Successful account login                            | T1078        |
| 09:15–09:16 | Workstation connects to unfamiliar external address | T1071        |
| 09:17       | BrowserUpdate.exe executes                          | T1204.002    |
| 09:18       | WinUpdateHelper scheduled task created              | T1053.005    |
| 09:22–09:24 | Finance and HR servers accessed                     | T1078        |
| 09:24:51    | Core Banking Server successfully accessed           | T1078        |
| 09:25       | External communication resumes                      | T1071        |

---

## Attack Chain

The incident can be summarized as:

**Phishing Email → Malicious Link → Credential Compromise → Valid Account Access → Endpoint Execution → Persistence → Lateral Movement → Core Banking Access**

---

## MITRE ATT&CK Mapping

The investigation identified several ATT&CK techniques:

### T1566.002 — Phishing: Spearphishing Link

The employee received an email impersonating IT Support and clicked the embedded link.

### T1204.001 — User Execution: Malicious Link

The attack required the employee to interact with the malicious link.

### T1078 — Valid Accounts

The compromised employee account was used to authenticate to internal systems.

### T1071 — Application Layer Protocol

The compromised workstation established outbound communication with an unfamiliar external address.

### T1204.002 — User Execution: Malicious File

`BrowserUpdate.exe` was executed on the workstation.

### T1053.005 — Scheduled Task/Job: Scheduled Task

`WinUpdateHelper` was created and executed to maintain persistence.

---

## Indicators of Compromise

| Indicator           | Type           | Context                            |
| ------------------- | -------------- | ---------------------------------- |
| `41.2.3.10`         | External IP    | Authentication activity            |
| `185.9.2.1`         | External IP    | Outbound workstation communication |
| `BrowserUpdate.exe` | File           | Suspicious executable              |
| `WinUpdateHelper`   | Scheduled Task | Persistence mechanism              |

---

## Root Cause

The investigation identified the primary root cause as insufficient authentication and security controls.

The compromised password was sufficient to authenticate to sensitive systems, including the Core Banking Server. Multi-factor authentication was not required.

Additional contributing gaps included:

* No documented security policy.
* No MFA requirement for sensitive systems.
* Insufficient email filtering.
* Lack of endpoint application controls.
* No defined incident escalation procedure.
* Limited monitoring coverage across the email gateway, firewall, and Core Banking Server.

---

## Impact Assessment

### Confidentiality

The compromised account was used to access Finance, HR, and Core Banking systems, placing sensitive customer and employee information at risk.

### Integrity

Access to the Core Banking Server created a risk of unauthorized modification of customer records or transactions. The investigation did not confirm unauthorized transactions during the compromise window.

### Availability

No system availability disruption was recorded during the incident.

---

## Incident Response

### Containment

* Disabled the compromised user account.
* Isolated the affected workstation.
* Blocked identified external IP addresses.

### Eradication

* Removed `BrowserUpdate.exe`.
* Removed the `WinUpdateHelper` scheduled task.
* Reset the user's credentials.
* Restored the workstation from a known-good image.

### Recovery

* Enrolled the user in MFA.
* Reviewed activity on Finance, HR, and Core Banking systems.
* Monitored the account for 14 days following restoration.

---

## Security Recommendations

The investigation resulted in several recommended security improvements:

### Identity & Access Management

* Implement MFA for remote access.
* Require MFA for the Core Banking Server.
* Apply stronger access-control policies.

### Email Security

* Deploy email filtering.
* Implement sender authentication checks.
* Inspect links contained in suspicious messages.

### Endpoint Security

* Implement application allow-listing.
* Block unsigned or unrecognized executables.
* Monitor creation of suspicious scheduled tasks.

### Monitoring & Detection

* Alert on authentication from unfamiliar external IP addresses.
* Monitor newly created scheduled tasks.
* Extend Wazuh monitoring to additional log sources.

### Network Security

* Separate user workstations from critical servers using network segmentation.
* Place Finance, HR, and Core Banking systems on separate VLANs.
* Apply firewall rules to restrict unnecessary communication between network segments.

### Security Awareness

* Conduct regular security awareness training.
* Run simulated phishing exercises.
* Train employees to identify spoofed IT-support communications.

---

## Network Segmentation

The investigation identified that the workstation and critical servers were located on the same network segment.

The proposed remediation separates user workstations from critical systems and introduces firewall controls between network segments.

This reduces the ability of a compromised workstation to directly reach sensitive servers.

---

## AI-Assisted Investigation

AI tools were used as part of the investigation workflow.

Co-Pilot was used to generate the raw log sources and phishing email screenshot.

Claude was used to assist with correlating separate log sources into a chronological timeline by cross-referencing timestamps, the employee identifier, and IP addresses.

AI-assisted analysis was used to support the investigation; the resulting timeline and findings were reviewed as part of the project.

---

## Skills Demonstrated

This project demonstrates practical experience with:

* Incident response
* Phishing investigation
* Log analysis
* Timeline reconstruction
* IOC identification
* MITRE ATT&CK
* Authentication analysis
* Endpoint investigation
* Network security
* Security monitoring
* Wazuh
* Vulnerability and security control analysis
* Network segmentation
* Incident containment and eradication
* Security recommendations

---

## Key Learning Outcome

The project demonstrated how multiple individual security events can be correlated to reconstruct an attack and identify security control gaps.

A key lesson from the investigation was that a successful phishing attack can become significantly more damaging when compromised credentials provide direct access to sensitive systems without an additional authentication layer.

---

## Limitations & Future Improvements

The available logs ended while the persistence mechanism was still active.

A future investigation would therefore examine:

* Possible data exfiltration.
* Additional lateral movement.
* Activity following the Core Banking Server login.
* Further endpoint activity associated with the persistence mechanism.
* Additional network and firewall telemetry.

---

## Project Documentation

The complete capstone report is available in the [`report`](./report/) directory.

---

## Disclaimer

This project is an educational cybersecurity case study based on a fictional organization.

The organization, infrastructure, users, IP addresses, and incident scenario are presented for educational and portfolio purposes.
