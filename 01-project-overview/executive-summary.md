# Executive Summary

# Executive Summary

## Project Overview

Programming Logic Unit Teardown & Operational Technology Security (PLUTOS) was a Disney-sponsored cybersecurity research project conducted through the California State University, Fullerton Center for Cybersecurity. The project focused on evaluating the security of Programmable Logic Controllers (PLCs) and Industrial Control Systems (ICS) commonly used within Operational Technology (OT) environments.

Disney Cybersecurity approached the CSUF Center for Cybersecurity to better understand PLC security, the industrial protocols that support these systems, and how a scalable cybersecurity strategy could be developed to protect them. To support this effort, Disney provided a testing environment designed to simulate aspects of a production industrial control system environment. The project team was tasked with assessing the environment from both an offensive and defensive cybersecurity perspective.

## Project Goals

The project was guided by three primary objectives:

1. Adapt and deploy a laboratory environment that replicates a Disney production-like Operational Technology environment.

2. Conduct a deep technical analysis of industrial protocols, communication flows, and PLC use cases relevant to Disney operations.

3. Develop a scalable cybersecurity strategy that incorporates PLC security into a broader Operational Technology security posture.

## Research Methodology

The assessment was performed using an Allen-Bradley Micro820 PLC, Cisco IE2000 Industrial Switch, Connected Components Workbench (CCW), and a collection of cybersecurity analysis tools.

The team evaluated the environment through several perspectives:

### Network Surface

The network surface assessment focused on understanding how PLC communications could be observed, intercepted, altered, or replayed by unauthorized devices connected to the same network.

Research activities included:

- EtherNet/IP and CIP protocol analysis
- Wireshark packet captures
- Network traffic inspection
- ARP spoofing testing
- Man-in-the-Middle (MITM) simulations
- Replay and packet manipulation analysis

### Control Surface

The control surface assessment evaluated whether authentication, authorization, or access-control mechanisms existed before PLC operations could be performed.

Research activities included:

- pycomm3 controller interaction
- PLC variable enumeration
- Runtime variable manipulation
- Unauthorized command testing
- Access-control validation

### Software and Firmware Surface

The software and firmware assessment examined the trust relationship between the PLC and engineering software used to manage it.

Research activities included:

- Connected Components Workbench (CCW) analysis
- Trusted software path evaluation
- Software compromise scenarios
- Firmware trust assumptions

## Key Findings

The assessment identified several important security considerations within the testing environment.

### CIP Communication Exposure

The PLC communicated using Common Industrial Protocol (CIP) over EtherNet/IP. Network communications were observable using standard packet analysis tools, allowing protocol behavior and controller interactions to be studied.

### Network-Based Attack Surface

Through ARP spoofing and MITM positioning, the team demonstrated the ability to intercept and monitor communications between engineering workstations and the PLC.

### Unauthorized Variable Manipulation

Using pycomm3 and custom testing scripts, PLC variables could be modified without traditional user authentication or role-based access controls. This demonstrated how unauthorized devices with network access could potentially influence controller behavior.

### Trusted Software Dependency

The assessment highlighted the importance of trusted engineering software such as Connected Components Workbench. Because PLCs inherently trust communications from authorized engineering tools, compromise of those tools could create additional security risks.

## Defensive Security Recommendations

Following the offensive assessment, the project shifted toward defensive security engineering and mitigation planning.

Recommended security controls included:

### Network Segmentation

Separate PLC devices into dedicated Operational Technology network segments and isolate them from unauthorized devices.

### Firewall and Access Control

Implement firewall rules and Access Control Lists (ACLs) to restrict access to PLC communication ports and allow only approved engineering workstations to communicate with controllers.

### Intrusion Detection and Monitoring

Deploy network monitoring and intrusion detection systems capable of identifying abnormal CIP communication patterns and unauthorized access attempts.

### Software Integrity Validation

Implement software integrity verification and change-management procedures to ensure trusted engineering software remains uncompromised.

## Project Outcome

The project successfully met all three objectives established by Disney Cybersecurity:

- Replicated a production-like PLC testing environment.
- Conducted an in-depth analysis of PLC communications and industrial protocols.
- Developed a scalable defensive strategy for improving PLC security.

The assessment provided practical experience in Operational Technology security, Industrial Control System security, protocol analysis, network defense, and cybersecurity architecture. The resulting research, demonstrations, and security recommendations contributed to a broader understanding of how PLC environments can be evaluated and protected against modern cybersecurity threats.

The project was recognized with the Best Sponsor Project Award at the California State University, Fullerton ECS Innovation Showcase.