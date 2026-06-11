# Operational Technology Security Assessment  
## Allen-Bradley Micro820 PLC | OT/ICS Cybersecurity Research

> **Winner of the CSUF ECS Innovation Showcase Best Sponsor Project Award** 🏆  
> Corporate-sponsored cybersecurity research project conducted in collaboration with **The Walt Disney Company**

---

## Project Overview

This repository documents a hands-on **Operational Technology (OT)** and **Industrial Control Systems (ICS)** cybersecurity assessment of an **Allen-Bradley Micro820 Programmable Logic Controller (PLC)**.

The project focused on evaluating how a PLC communicates across an industrial network, identifying weaknesses in PLC communication, testing read/write access to controller variables, and designing defensive controls to reduce risk in OT environments.

Testing was conducted in a controlled lab environment using authorized hardware and tools. The assessment demonstrated how weak or missing security controls in PLC environments can allow unauthorized communication, traffic interception, and controller variable manipulation.

---

## Project Poster

![ECS Expo Poster](https://github.com/samahorro/Micro820-OT-ICS-Security-Assessment/blob/f7390ce0447109ec16d8b3275ed49d21739460bd/img/ECS%20Expo%20Poster.png?raw=true)

---

## Why This Project Matters

PLCs are used to control critical physical systems across industries such as manufacturing, healthcare, utilities, transportation, and entertainment infrastructure.

Unlike traditional IT systems, many PLCs prioritize availability, reliability, and real-time control over built-in cybersecurity protections. As a result, insecure PLC communication can create serious risks, including:

- Unauthorized access to industrial devices
- Loss of process integrity
- Cleartext exposure of control traffic
- Manipulation of controller variables
- Increased risk of disruption to physical operations

This project highlights the importance of applying cybersecurity principles to OT and ICS environments where digital compromise can affect physical systems.

---

## Key Cybersecurity Skills Demonstrated

- Operational Technology Security
- Industrial Control Systems Security
- PLC Security Assessment
- EtherNet/IP and CIP Protocol Analysis
- Network Traffic Inspection
- Packet Capture and Analysis
- Unauthorized Access Testing
- MITM Risk Analysis
- ARP Spoofing and ARP Poisoning Analysis
- PLC Command Manipulation Testing
- Controller Variable Read/Write Testing
- Network Segmentation Design
- Firewall and ACL Planning
- IDS/IPS Monitoring Concepts
- Defense-in-Depth Architecture
- Risk Assessment and Mitigation Planning
- Technical Documentation and Research Presentation

---

## Lab Environment

The assessment was performed using a controlled OT lab environment that simulated a real-world PLC network.

### Hardware and Infrastructure

- Allen-Bradley Micro820 PLC
- Cisco industrial Ethernet switch
- Windows engineering workstation
- Kali Linux attacker/test workstation
- Isolated OT lab network
- VMware virtualized testing environment

### Tools Used

- Kali Linux
- Wireshark
- Ettercap
- arp-scan
- pylogix
- pycomm3
- Scapy
- Connected Components Workbench
- pfSense
- VMware

---

## Project Goals

The main goals of this project were to assess the cybersecurity impact of weak protections in PLC systems by:

- Identifying vulnerabilities in PLC communication and architecture
- Analyzing EtherNet/IP and CIP traffic between the workstation and PLC
- Testing read/write access to controller variables during runtime
- Simulating real-world attack scenarios such as MITM and PLC command manipulation
- Observing physical PLC behavior during control manipulation
- Designing defensive recommendations for securing PLC environments

---

## Methodology

Testing focused on three primary layers of the PLC environment.

### 1. PLC Layer

The PLC layer focused on controller behavior, firmware interaction, ladder logic execution, and runtime variable access.

Testing included:

- Observing ladder logic execution
- Reading controller variables
- Writing to controller variables
- Monitoring changes in physical PLC behavior
- Assessing whether access required authentication
- Evaluating possible PLC logic exposure through engineering software and firmware-level access

### 2. Network Layer

The network layer focused on how the PLC communicated with engineering systems over EtherNet/IP and how traffic could be observed within the lab environment.

Testing included:

- Identifying devices on the OT subnet using ARP table analysis and `arp-scan`
- Mapping the PLC, Windows engineering workstation, Kali test system, and Cisco switch within the lab network
- Capturing EtherNet/IP traffic between the workstation and PLC using Wireshark
- Reviewing CIP request and response traffic
- Observing cleartext PLC communication
- Analyzing how VMware bridged networking exposed PLC traffic to the test environment
- Testing ARP spoofing and MITM conditions using Ettercap

### 3. Attack Surface Layer

The attack surface layer focused on how an unauthorized system could interact with the PLC if placed on the same network.

Testing included:

- MITM testing using ARP spoofing
- ARP poisoning analysis
- Packet capture and protocol inspection
- Controller variable interaction using Python-based PLC communication libraries
- PLC command manipulation testing in a lab environment
- Assessing authentication and access control weaknesses

---

## Key Findings

| Area | Finding | Security Impact |
|---|---|---|
| Network Surface | PLC communication was reachable from systems on the OT network | Unauthorized devices could attempt communication if network access is obtained |
| EtherNet/IP / CIP | Communication occurred in cleartext | Control traffic and data could be captured and analyzed |
| Authentication / Access Control | Read/write interaction did not require credentials in the tested lab configuration | Unauthorized systems on the OT network could interact with PLC variables |
| Control Surface | Controller variables could be modified during runtime | Potential loss of integrity and unsafe process behavior |
| MITM Risk | ARP spoofing allowed traffic interception in the lab network | Increased risk of traffic manipulation or observation |
| Virtualization Exposure | VMware bridged networking allowed PLC traffic to be observed from the test environment | Misconfigured virtual networking can unintentionally expose OT traffic |
| Firmware / CCW Layer | PLC logic exposure was identified as a possible risk | Sensitive control logic may be accessible if protections are not enforced |

---

## Demonstrated Security Risks

The assessment demonstrated several major OT security risks:

- Unauthorized PLC access
- Cleartext industrial communication
- Lack of authentication for tested read/write operations
- Runtime controller variable manipulation
- Loss of integrity in PLC-controlled processes
- Data exposure through packet capture
- Man-in-the-middle risk using ARP spoofing
- ARP poisoning risk in trusted OT network segments
- Weak network trust boundaries
- Potential PLC logic exposure through engineering software or firmware-level access

---

## Example Testing Focus

This project included authorized testing of PLC communication using Python-based industrial communication libraries.

Testing focused on whether controller variables could be read or modified from an external system within the lab network.

```python
from pycomm3 import LogixDriver

PLC_IP = "192.168.0.10"

with LogixDriver(PLC_IP) as plc:
    result = plc.read("example_tag")
    print(result)
```

> This example represents authorized lab testing used to validate whether PLC variables could be accessed from an external system on the same OT network.

---

## Defensive Architecture

Based on the findings, a defense-in-depth architecture was designed to reduce PLC exposure and restrict unauthorized communication.

Recommended controls included:

- Firewall rules to restrict PLC access to trusted engineering systems
- ACLs to limit communication to approved devices
- VLAN segmentation to isolate PLCs from unauthorized networks
- IDS/IPS monitoring for suspicious industrial traffic
- Real-time alerting for unexpected CIP communication
- Monitoring for unauthorized write operations
- Restricting engineering software access
- Applying vendor hardening guidance
- Evaluating CIP Security or Secure EtherNet/IP where supported

---

## Recommended Mitigations

| Risk | Recommended Mitigation |
|---|---|
| Unauthorized PLC communication | Restrict access using firewall rules and ACLs |
| Flat OT network exposure | Segment PLCs into dedicated OT VLANs |
| Cleartext communication | Use secure industrial protocols where supported |
| Unauthorized variable writes | Limit write access to approved engineering workstations |
| MITM attacks | Use network segmentation, static ARP where appropriate, port security, and monitoring |
| ARP poisoning | Monitor for duplicate ARP entries and unexpected MAC/IP mappings |
| Lack of visibility | Deploy IDS/IPS monitoring for EtherNet/IP and CIP traffic |
| Firmware or logic exposure | Apply vendor hardening guidance and restrict CCW access |
| Excessive trust between devices | Implement zero-trust principles where practical in OT environments |

---

## Project Outcomes

The team developed a PLC security testing framework that evaluated vulnerabilities across the network, control, and firmware layers.

Testing confirmed that in the lab configuration:

- PLC communication could be captured and analyzed
- EtherNet/IP and CIP traffic occurred in cleartext
- Read/write operations could be performed without credentials
- Controller variables could be modified during runtime
- PLC behavior could be influenced through unauthorized interaction
- ARP spoofing could create MITM conditions in the lab network
- VMware bridged networking could expose PLC traffic to a virtualized test system
- Defensive controls such as segmentation, firewall rules, ACLs, port security, and monitoring are necessary to reduce risk

---

## Recruiter Highlights

This project demonstrates hands-on cybersecurity experience in OT/ICS environments, including protocol analysis, network security testing, PLC interaction, and defensive architecture design.

Relevant security areas demonstrated:

- OT/ICS cybersecurity assessment
- Network security and segmentation
- Protocol analysis using Wireshark
- PLC communication testing
- Access control evaluation
- MITM and ARP spoofing analysis
- Risk identification and mitigation planning
- Defense-in-depth architecture design
- Technical documentation and research presentation

Relevant roles this project aligns with:

- Security Engineer
- OT Security Analyst
- ICS Security Analyst
- Network Security Engineer
- Cybersecurity Analyst
- Detection Engineer
- Vulnerability Management Analyst
- Infrastructure Security Engineer

---

## Responsible Use

This repository is intended for educational purposes, defensive security research, and authorized laboratory testing only.

All testing was conducted in a controlled lab environment using approved equipment. This project does not include destructive attack automation, production system testing, or sensitive industrial data.

Do not use any techniques, scripts, or testing methods from this repository against systems you do not own or have explicit permission to assess.

---

## Contributors

- Samantha Ahorro
- Matthew Garabedian
- Ryan Hartwig

### Project Mentors

- Dr. Mikhail Gofman
- Prof. Michael Franklin

### Acknowledgments

Special thanks to **The Walt Disney Company**, the **CSUF Center for Cybersecurity**, and the **CSUF College of Engineering and Computer Science** for supporting this project.
