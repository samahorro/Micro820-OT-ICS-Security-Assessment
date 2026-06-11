# Operational Technology Security Assessment  
## Allen-Bradley Micro820 PLC | OT/ICS Cybersecurity Research

> 🏆 **Winner of the CSUF ECS Innovation Showcase Best Sponsor Project Award**  
> Corporate-sponsored cybersecurity research project conducted in collaboration with **The Walt Disney Company**

---

## Project Overview

This repository documents a hands-on **Operational Technology (OT)** and **Industrial Control Systems (ICS)** cybersecurity assessment of an **Allen-Bradley Micro820 Programmable Logic Controller (PLC)**.

The project focused on evaluating how a PLC communicates across an industrial network, identifying weaknesses in PLC communication, testing read/write access to controller variables, and designing defensive controls to reduce risk in OT environments.

Testing was conducted in a controlled lab environment using authorized hardware and tools. The assessment demonstrated how weak or missing security controls in PLC environments can allow unauthorized communication, traffic interception, and control variable manipulation.

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
- Command Injection Testing
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
- Industrial Ethernet switch
- Engineering workstation
- Attacker/test workstation
- Isolated lab network

### Tools Used

- Kali Linux
- Wireshark
- pylogix
- pycomm3
- Ettercap
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
- Simulating real-world attack scenarios such as MITM and command injection
- Observing physical PLC behavior during control manipulation
- Designing defensive recommendations for securing PLC environments

---

## Methodology

Testing focused on three primary layers of the PLC environment.

### 1. PLC Layer

The PLC layer focused on controller behavior, firmware interaction, and runtime variable access.

Testing included:

- Observing ladder logic execution
- Reading controller variables
- Writing to controller variables
- Monitoring changes in physical PLC behavior
- Assessing whether access required authentication

### 2. Network Layer

The network layer focused on how the PLC communicated with engineering systems over EtherNet/IP.

Testing included:

- Capturing EtherNet/IP traffic over TCP port `44818`
- Analyzing CIP request and response traffic
- Reviewing cleartext communication between the workstation and PLC
- Identifying protocol-level exposure
- Observing how industrial traffic could be intercepted in the lab network

### 3. Attack Surface Layer

The attack surface layer focused on how an unauthorized system could interact with the PLC if placed on the same network.

Testing included:

- MITM testing using ARP spoofing
- Packet capture and inspection
- Controller variable interaction using Python libraries
- Command injection testing in a lab environment
- Assessing access control weaknesses

---

## Key Findings

| Area | Finding | Security Impact |
|---|---|---|
| Network Surface | PLC communication was reachable from systems on the OT network | Unauthorized devices could attempt communication if network access is obtained |
| EtherNet/IP / CIP | Communication occurred in cleartext | Control traffic and data could be captured and analyzed |
| Authentication | Read/write interaction did not require credentials in the tested lab configuration | Unauthorized access risk if network segmentation is weak |
| Control Surface | Controller variables could be modified during runtime | Potential loss of integrity and unsafe process behavior |
| MITM Risk | ARP spoofing allowed traffic interception in the lab network | Increased risk of traffic manipulation or observation |
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
- Weak network trust boundaries

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
