# Attack Analysis

## Initial Access

The attack began with a spoofed IT-support email sent to a Finance Department employee. The employee clicked the link, providing the initial user interaction that enabled the compromise.

## Credential Compromise

A failed login from external IP `41.2.3.10` was followed shortly afterward by a successful login for the same account. The report identifies this sequence as evidence of credential compromise.

## Endpoint Activity

The workstation subsequently communicated with unfamiliar external address `185.9.2.1`. `BrowserUpdate.exe` then appeared and executed on the workstation.

## Persistence

A scheduled task named `WinUpdateHelper` was created and started. The task remained active later in the timeline.

## Lateral Movement / Internal Access

The compromised employee account accessed Finance and HR servers and then successfully authenticated to the Core Banking Server at 09:24:51.

## Impact

The report identified risks to confidentiality and integrity because sensitive systems were accessed. No confirmed unauthorized transactions were identified during the compromise window, and no availability disruption was recorded.

## Root Cause

The primary root cause identified in the report was the absence of a written security policy or technical control requiring more than a password to reach sensitive systems. Contributing gaps included insufficient email filtering, missing endpoint controls, and the absence of a documented incident response procedure.
