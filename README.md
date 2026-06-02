# Operational Technology (OT) & Industrial Control Systems (ICS) Security Assessment of an Allen-Bradley Micro820 PLC

> 🏆 Winner of the CSUF ECS Innovation Showcase Best Sponsor Project Award
>
> Corporate-sponsored cybersecurity research project conducted in collaboration with **The Walt Disney Company**.

This repository documents a hands-on Operational Technology (OT) and Industrial Control Systems (ICS) cybersecurity assessment of an Allen-Bradley Micro820 Programmable Logic Controller (PLC). The project evaluates the security posture of industrial communications through protocol analysis, controller interaction testing, network security assessment, and defensive architecture design.

The assessment focuses on:

- Common Industrial Protocol (CIP)
- EtherNet/IP Communications
- Operational Technology (OT) Security
- Industrial Control Systems (ICS) Security
- PLC Network Exposure Analysis
- Authentication and Access Control Evaluation
- Controller Variable Manipulation via pycomm3
- Packet Capture and Protocol Analysis using Wireshark
- Replay-Risk Indicators and Session Analysis
- Firewall-Based Security Controls using pfSense
- Network Segmentation and Defense-in-Depth
- CIP Security and Secure EtherNet/IP Mitigations

---

## Overview

Industrial Control Systems (ICS) and Operational Technology (OT) environments often rely on legacy communication protocols that prioritize reliability and deterministic communications over modern cybersecurity protections.

This project investigates the security implications of those design assumptions through hands-on analysis of an Allen-Bradley Micro820 PLC operating within a controlled laboratory environment.

The hardware environment, including the PLC and supporting industrial networking infrastructure, was provided through a corporate-sponsored initiative by **The Walt Disney Company**. The objective was to evaluate industrial communication security, identify potential attack surfaces, analyze protocol behavior, and develop practical defensive strategies for securing PLC-based environments.

---

## Key Skills Demonstrated

- Industrial Control System (ICS) Security
- Operational Technology (OT) Security
- Network Security Assessment
- Protocol Analysis & Packet Inspection
- Common Industrial Protocol (CIP) Analysis
- EtherNet/IP Security Research
- PLC Communications & Controller Interaction
- Threat Modeling & Risk Assessment
- Security Architecture & Defense-in-Depth
- Firewall Design & Network Segmentation
- Security Monitoring & Detection Engineering
- Vulnerability Assessment Methodologies

---

## Technologies Used

- Allen-Bradley Micro820 PLC
- Cisco Industrial Ethernet Switch
- Kali Linux
- pycomm3
- Wireshark
- Nmap
- VMware
- pfSense
- Connected Components Workbench (CCW)

---

## Key Findings

| Area | Finding | Security Impact |
|--------|--------|--------|
| Network Surface | PLC communication was reachable from devices on the OT network | Increased exposure if network access is obtained |
| CIP Protocol | Session-based request/response communication observed | Security depends on access controls and session protections |
| Authentication | No obvious credential exchange observed before protocol interaction | Unauthorized devices may communicate if network access exists |
| Control Surface | pycomm3 successfully interacted with controller variables in a lab environment | Potential loss of process integrity |
| Replay Risk | Replay susceptibility depends on session validation and authentication mechanisms | Weak protections may increase replay risk |
| Mitigation | Firewall segmentation and allowlists can restrict access to industrial services | Reduces unauthorized protocol interaction |

---

## Recommended Mitigations

- Segment PLCs into dedicated OT security zones
- Deploy firewall allowlists for industrial communication ports
- Restrict access to approved engineering and HMI systems
- Enable controller authentication and role-based access where supported
- Implement CIP Security / Secure EtherNet/IP where available
- Monitor for unexpected CIP sessions and write operations
- Disable unused services and communication paths
- Apply firmware updates and vendor hardening guidance

---

## Project Impact

This project demonstrates the application of cybersecurity principles within industrial control environments by analyzing protocol behavior, evaluating potential security weaknesses, and designing layered defensive controls.

The work provides practical experience with:

- PLC Security
- OT Security
- ICS Security
- Protocol Analysis
- Industrial Networking
- Threat Modeling
- Security Architecture
- Network Segmentation
- Firewall Engineering
- Defensive Cybersecurity

These skills are commonly required within critical infrastructure, industrial cybersecurity, security engineering, and operational technology security roles.

---

## Responsible Use

This repository is intended for educational purposes, defensive security research, and authorized laboratory testing only.

No destructive attack automation, production system testing, or sensitive industrial data is included within this repository.

All research was conducted in a controlled lab environment using authorized hardware and equipment.

---

## Project Status

- ✅ Network and protocol analysis completed
- ✅ Wireshark packet analysis completed
- ✅ pycomm3 interaction testing completed
- 🔄 Replay-risk assessment ongoing
- 🔄 pfSense implementation and validation in progress
- 📋 Final mitigation testing planned
