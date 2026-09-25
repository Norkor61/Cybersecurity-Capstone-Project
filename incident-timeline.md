# Incident Timeline

The timeline was reconstructed by correlating email, authentication, endpoint process, and network connection logs.

| Time | Event | MITRE ATT&CK |
|---|---|---|
| 09:12 | Employee receives an email spoofed to appear from IT Support, requesting an urgent browser security update. | T1566.002 — Phishing: Spearphishing Link |
| 09:13 | Employee clicks the link contained in the email. | T1204.001 — User Execution: Malicious Link |
| 09:14 | Failed login attempt recorded for the employee account from external IP `41.2.3.10`. | T1078 — Valid Accounts |
| 09:14:47 | Successful login for the same account from the same external IP, indicating credential compromise. | T1078 — Valid Accounts |
| 09:15–09:16 | Workstation establishes two outbound connections to unfamiliar external address `185.9.2.1`. | T1071 — Application Layer Protocol |
| 09:17 | Suspicious executable `BrowserUpdate.exe` appears and is executed. | T1204.002 — User Execution: Malicious File |
| 09:18 | Scheduled task `WinUpdateHelper` is created and started. | T1053.005 — Scheduled Task/Job |
| 09:22–09:24 | Employee account accesses Finance and HR servers, then attempts to access the Core Banking Server. | T1078 — Valid Accounts |
| 09:24:51 | Successful login to the Core Banking Server under the employee account. | T1078 — Valid Accounts |
| 09:25 | Workstation communicates with `185.9.2.1` again. | T1071 — Application Layer Protocol |
| 09:26 | `WinUpdateHelper` scheduled task remains active. | T1053.005 — Scheduled Task/Job |

## Key Observation

The timeline shows how a phishing event progressed rapidly from initial user interaction to credential use, endpoint execution, persistence, internal access, and successful access to the Core Banking Server.
