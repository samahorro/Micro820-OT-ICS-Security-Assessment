## Network Topology

The simulated production environment consisted of an Allen-Bradley Micro820 PLC connected to a Cisco IE2000 Industrial Switch and multiple engineering workstations operating within the same OT network segment.

The PLC was configured at **192.168.0.10** and communicated using **CIP over EtherNet/IP**, while engineering workstations at **192.168.0.13**, **192.168.0.22**, and **192.168.0.50** were used for controller programming, protocol analysis, packet inspection, and cybersecurity assessment activities.

This environment enabled hands-on research into Industrial Control System (ICS) security, including network reconnaissance, protocol analysis, controller interaction through pycomm3, packet capture using Wireshark, and the evaluation of defensive security controls. The architecture served as the foundation for identifying OT attack surfaces and designing mitigation strategies such as network segmentation, firewall enforcement, and defense-in-depth security controls.

![img alt](https://github.com/samahorro/Micro820-OT-ICS-Security-Assessment/blob/823bd0884c78b1d2ddac5c4532558fea068be27a/img/Network%20Topology%20of%20Simulated%20Production%20Enviroment.png)

## System Design

The simulated production environment was designed to emulate a small-scale Operational Technology (OT) network commonly found in industrial control environments. The architecture consisted of an Allen-Bradley Micro820 PLC connected to a Cisco IE2000 Industrial Ethernet Switch, which served as the central communication point between the controller and engineering workstations.

The Micro820 PLC functioned as the primary control device within the environment and was assigned the IP address **192.168.0.10**. The controller communicated using the **Common Industrial Protocol (CIP)** over **EtherNet/IP**, allowing engineering systems to monitor, read, and modify controller variables.

The Cisco IE2000 Industrial Switch provided Layer 2 connectivity between all devices and simulated the industrial networking infrastructure commonly deployed within Operational Technology environments. The switch allowed engineering workstations and the PLC to communicate within the same subnet, enabling protocol analysis and controller interaction testing.

Three engineering workstations were deployed within the Engineering Zone:

| Device | IP Address | Purpose |
|----------|----------|----------|
| Engineering Workstation | 192.168.0.13 | Controller programming and monitoring |
| Security Analysis Workstation | 192.168.0.22 | Packet capture and protocol analysis |
| Cybersecurity Testing Workstation | 192.168.0.50 | Security validation and controller interaction testing |

The engineering workstations represented systems that would normally be used by operators, engineers, and administrators responsible for managing industrial processes. These systems were used throughout the assessment to observe network traffic, analyze CIP communications, interact with PLC variables, and evaluate the effectiveness of security controls.

The flat network architecture intentionally allowed all devices to communicate directly with the PLC. This design enabled the project team to study protocol behavior, identify potential attack surfaces, evaluate access-control mechanisms, and assess the security implications of unrestricted controller access.

The environment served as the baseline architecture for both offensive security assessments and defensive security engineering activities. Findings from this architecture were later used to develop mitigation strategies including network segmentation, firewall enforcement through pfSense, controller access restrictions, and defense-in-depth security controls.
