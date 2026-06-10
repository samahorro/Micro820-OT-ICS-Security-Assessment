# Defense-in-Depth Architecture

## Overview

The Defense-in-Depth Architecture was developed as a recommended security design for protecting Operational Technology (OT) and Industrial Control System (ICS) environments against unauthorized access, network-based attacks, and protocol abuse. The architecture applies multiple layers of security controls to reduce the likelihood that a single failure could compromise critical industrial assets.

The design was developed based on observations and findings gathered during the Micro820 PLC security assessment and demonstrates how organizations can implement layered security controls to protect PLCs and industrial communication networks.

![[Defense-in-Depth Architecture](../img/defense-in-depth-architecture.png](https://github.com/samahorro/Micro820-OT-ICS-Security-Assessment/blob/c2c771f41ed9c440a618304500520370c8fbc1ab/img/Defense-In-Depth%20Architecture.png)

---

## Architecture Components

### Trusted Engineering Network

The Trusted Engineering Network contains authorized engineering workstations used for PLC programming, maintenance, monitoring, and operational support activities.

Only approved systems are permitted to communicate with industrial assets. Access from this network is restricted through firewall policies and network access controls.

**Security Objectives**

- Restrict PLC access to authorized personnel
- Prevent unauthorized engineering workstation connections
- Reduce the attack surface exposed to critical industrial devices

---

### Firewall and Access Control Layer

The firewall serves as the primary security boundary between engineering systems and the industrial control network.

Access Control Lists (ACLs) are configured to permit only approved hosts and required protocols, such as CIP and EtherNet/IP communications, while denying all unauthorized traffic.

**Security Controls**

- IP-based allowlists
- Port restrictions
- Protocol filtering
- Network segmentation enforcement
- Logging and auditing

**Threats Mitigated**

- Unauthorized CIP access
- pycomm3-based controller interaction
- Unauthorized variable manipulation
- External network reconnaissance

---

### Industrial Switch Infrastructure

The industrial switch provides network connectivity between authorized devices and industrial assets.

In addition to forwarding traffic, the switch can be configured to mirror network traffic through a SPAN (Switch Port Analyzer) or mirror port, enabling passive security monitoring without interfering with operational communications.

**Security Controls**

- VLAN segmentation
- Port security
- Traffic mirroring
- Network visibility

---

## IDS/IPS Monitoring Layer

An Intrusion Detection System/Intrusion Prevention System was implemented using **Suricata** with **EveBox** as the alert monitoring dashboard. This layer monitors traffic within the industrial control system network and identifies suspicious or unauthorized communication attempts involving the PLC.

Traffic mirrored from the switch was analyzed to detect abnormal communication patterns, unauthorized EtherNet/IP and CIP activity, ICMP scanning, and possible reconnaissance attempts against the PLC. EveBox provided centralized visibility into Suricata alerts, allowing security events to be reviewed, filtered, and investigated from a single dashboard.

As shown in the monitoring dashboard, Suricata generated multiple alerts related to PLC communication, including **Unauthorized EtherNet/IP Access Attempts**, **PLC EtherNet/IP CIP Traffic Detected**, **Unauthorized Ping Attempts to PLC**, and **Local ICMP Ping Detected**. These alerts demonstrate that the IDS was able to identify suspicious traffic targeting the PLC at `192.168.0.10`.

### Figures

**Figure 1:** EveBox dashboard showing alert activity over time and the most frequent IDS signatures.

![IDS Alert System](https://github.com/samahorro/Micro820-OT-ICS-Security-Assessment/blob/a8d6ef930e411082241cb7f368625d84dd09b201/img/IDS%20Alert%20System.png)

**Figure 2:** EveBox analytics dashboard displaying event types, protocols, and top alert signatures.

![SIEM Dashboard Overview](https://github.com/samahorro/Micro820-OT-ICS-Security-Assessment/blob/dc631fceb5f21cf902c4ab95e88a0274896ab751/img/SIEM%20Dashboard%20Overview.png)

**Figure 3:** EveBox alert showing an unauthorized ping attempt from `192.168.0.44` to the PLC at `192.168.0.10`, indicating possible reconnaissance activity against the controller.

**Figure 4:** Suricata/EveBox alert view displaying detected PLC-related events such as ICMP ping detection and EtherNet/IP CIP traffic.

---

**Security Controls**

- Protocol-aware inspection
- Signature detection
- Behavioral analysis
- Alert generation
- Automated blocking (IPS mode)

**Threats Mitigated**

- Unauthorized controller access
- Replay attack attempts
- Network scanning
- Denial-of-Service activity
- Suspicious CIP write operations

---

### Monitoring and Management System

The Monitoring and Management System provides centralized visibility into the OT environment.

Security events, alerts, logs, and operational metrics are collected and reviewed to support incident response and continuous monitoring activities.

**Security Controls**

- Centralized logging
- Security monitoring
- Event correlation
- Alert management
- Operational visibility

---

### Isolated PLC Network

The PLC Network contains the most critical industrial assets, including PLCs and Human-Machine Interfaces (HMIs).

This network segment is isolated from general-purpose systems and can only be accessed through approved pathways.

**Protected Assets**

- Allen-Bradley Micro820 PLCs
- Human-Machine Interfaces (HMIs)
- Industrial control devices
- Operational process data

**Security Objectives**

- Prevent direct attacker access
- Limit protocol exposure
- Protect industrial operations
- Maintain process integrity and availability

---

## Security Benefits

The Defense-in-Depth Architecture provides multiple layers of protection for industrial environments:

- Network segmentation reduces exposure of PLCs to unauthorized devices.
- Firewall policies restrict controller access to approved engineering systems.
- IDS/IPS monitoring detects and alerts on suspicious activity.
- Continuous monitoring improves visibility into industrial communications.
- Isolated OT zones reduce the likelihood of lateral movement.
- Multiple security controls prevent a single point of failure.

---

## Relation to Assessment Findings

During the security assessment, the PLC environment operated on a flat network where devices could directly communicate with the controller. This allowed protocol analysis, controller interaction testing, and evaluation of potential attack paths.

The Defense-in-Depth Architecture represents a recommended future-state design intended to address identified risks by introducing layered security controls, network segmentation, monitoring capabilities, and access restrictions around critical industrial assets.

Key findings that influenced this design included:

- Direct PLC access from devices located on the same network segment
- Successful CIP communication analysis using Wireshark
- PLC interaction through pycomm3
- Evaluation of authentication and access-control limitations
- Analysis of replay-risk indicators within industrial communications
- Assessment of potential network-based attack paths

---

## Conclusion

A layered security strategy is essential for protecting modern Operational Technology environments. By combining network segmentation, firewall enforcement, IDS/IPS monitoring, centralized visibility, and isolated PLC networks, organizations can significantly reduce the risk of unauthorized access, protocol abuse, and operational disruption while maintaining the reliability and availability required by industrial systems.
