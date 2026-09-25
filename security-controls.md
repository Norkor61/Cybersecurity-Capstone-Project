# Security Controls & Remediation Plan

## 1. Identity and Access Management

**Gap:** A compromised password was sufficient to reach sensitive systems.

**Recommendation:**
- Require MFA on remote logins.
- Require MFA specifically for the Core Banking Server.
- Strengthen access-control policies.

## 2. Email Security

**Gap:** The spoofed IT-support email reached the employee without an alert.

**Recommendation:**
- Deploy email filtering.
- Use sender authentication checks.
- Inspect links in suspicious messages.

## 3. Endpoint Security

**Gap:** `BrowserUpdate.exe` was able to execute.

**Recommendation:**
- Deploy application allow-listing or similar endpoint application controls.
- Block unsigned or unrecognized executables.
- Monitor suspicious scheduled task creation.

## 4. Monitoring and Detection

**Gap:** The failed-then-successful external login was not escalated before sensitive-system access.

**Recommendation:**
- Alert on authentication from unfamiliar external IP addresses.
- Alert on newly created scheduled tasks.
- Extend Wazuh coverage to additional relevant log sources.

## 5. Network Security

**Gap:** The affected workstation and critical servers were on the same network segment.

**Recommendation:**
- Separate user workstations from critical servers.
- Use separate VLANs.
- Apply firewall rules restricting unnecessary host-to-host communication.

## 6. Security Awareness

**Recommendation:**
- Conduct refresher security awareness training.
- Run simulated phishing exercises.
- Focus training on spoofed IT-support communications.

## 7. Incident Response

**Gap:** No documented incident response procedure existed at the time of the incident.

**Recommendation:**
- Adopt a formal Incident Response Policy.
- Define escalation triggers.
- Document roles and response procedures.
