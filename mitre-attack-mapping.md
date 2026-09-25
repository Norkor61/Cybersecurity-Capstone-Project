# MITRE ATT&CK Mapping

| Technique | Name | Observed Activity |
|---|---|---|
| T1566.002 | Phishing: Spearphishing Link | Spoofed IT-support email contained a malicious link. |
| T1204.001 | User Execution: Malicious Link | Employee clicked the phishing link. |
| T1078 | Valid Accounts | Compromised employee credentials were used for authentication. |
| T1071 | Application Layer Protocol | Workstation communicated with an unfamiliar external address. |
| T1204.002 | User Execution: Malicious File | `BrowserUpdate.exe` was executed. |
| T1053.005 | Scheduled Task/Job: Scheduled Task | `WinUpdateHelper` was created and started for persistence. |

## Attack Flow

**T1566.002 → T1204.001 → T1078 → T1071 → T1204.002 → T1053.005 → T1078**

The mapping is based only on techniques explicitly identified in the capstone report.
