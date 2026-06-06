# Tooling

This section documents the tools used during the OT/ICS security assessment. The tools supported network discovery, traffic analysis, PLC communication review, controlled attack testing, and defensive monitoring.

## Tools Used

| Tool | Purpose |
|---|---|
| Wireshark | Captured and analyzed network traffic between OT/ICS devices. |
| Nmap | Identified active hosts, open ports, and exposed services in the lab network. |
| Scapy | Supported packet crafting and controlled network testing. |
| Ettercap | Used to demonstrate man-in-the-middle behavior in the simulated lab environment. |
| Connected Components Workbench | Used to interact with and review Micro820 PLC logic and configuration. |
| Suricata | Used to explore defensive monitoring and detection rule opportunities. |
| Kali Linux | Used as the security testing workstation for assessment tools. |

## Tooling Purpose

The tooling was selected to support both offensive and defensive analysis.

From the offensive side, the tools helped identify exposed services, observe insecure communication, and demonstrate possible attack paths within the simulated OT/ICS environment.

From the defensive side, the tools helped evaluate how network monitoring, detection rules, and improved segmentation could reduce risk and improve visibility.

## Testing Notes

All tools were used only within a controlled lab environment. No testing was performed against production systems, public networks, or unauthorized environments.
