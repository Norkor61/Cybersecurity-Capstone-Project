# Network Segmentation

## Before Segmentation

The report describes a network where the affected laptop and the Ubuntu Server hosting Finance, HR, and Core Banking systems were on the same `10.10.10.0/26` segment behind a single switch.

This arrangement allowed the compromised workstation to reach sensitive systems directly.

## Proposed Improvement

Separate user workstations and critical servers into different network segments/VLANs and enforce communication through firewall rules.

Example conceptual design:

```text
                 Internet
                    |
                 Firewall
                    |
          +---------+---------+
          |                   |
       User VLAN          Server VLAN
          |                   |
     Finance Laptop     +-----+------+
                        |            |
                   Finance/HR   Core Banking
                    Servers       Server
```

## Security Benefit

The report's recommendation is intended to prevent a compromised user workstation from directly reaching critical servers without passing through appropriate network controls.

> This diagram is a conceptual representation of the report's proposed segmentation, not a production network configuration.
