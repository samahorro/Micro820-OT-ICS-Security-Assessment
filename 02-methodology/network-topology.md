## Network Topology

The simulated production environment consisted of an Allen-Bradley Micro820 PLC connected to a Cisco IE2000 Industrial Switch and multiple engineering workstations operating within the same OT network segment.

The PLC was configured at **192.168.0.10** and communicated using **CIP over EtherNet/IP**, while engineering workstations at **192.168.0.13**, **192.168.0.22**, and **192.168.0.50** were used for controller programming, protocol analysis, packet inspection, and cybersecurity assessment activities.

This environment enabled hands-on research into Industrial Control System (ICS) security, including network reconnaissance, protocol analysis, controller interaction through pycomm3, packet capture using Wireshark, and the evaluation of defensive security controls. The architecture served as the foundation for identifying OT attack surfaces and designing mitigation strategies such as network segmentation, firewall enforcement, and defense-in-depth security controls.

![img alt](https://github.com/samahorro/Micro820-OT-ICS-Security-Assessment/blob/823bd0884c78b1d2ddac5c4532558fea068be27a/img/Network%20Topology%20of%20Simulated%20Production%20Enviroment.png)
