# Indicators of Compromise

The following indicators were identified in the incident report.

| Indicator | Type | Context |
|---|---|---|
| `41.2.3.10` | External IP address | Failed and successful authentication activity |
| `185.9.2.1` | External IP address | Outbound workstation communication |
| `BrowserUpdate.exe` | Suspicious executable | Executed on the affected workstation |
| `WinUpdateHelper` | Scheduled task | Persistence mechanism |

## Handling Notes

These indicators are documented as part of a fictional educational scenario. Do not treat them as confirmed malicious infrastructure outside the scenario.

When publishing a real-world incident to a public repository, remove or anonymize sensitive indicators where required by organizational policy.
