# Results and Outcomes

The project successfully replicated a PLC testing environment similar to the Disney-provided production environment and used it to evaluate PLC security risks. The team confirmed that the Micro820 PLC communicated over the local network using EtherNet/IP/CIP traffic, which allowed the workstation and PLC to exchange read/write commands.

During the MITM and command injection demonstration, the PLC accepted an injected command as valid. The attacker-controlled value overrode the operator’s intended value, showing that an unauthorized device on the network could affect PLC behavior if proper protections were not in place. Specifically, the PLC variable `g_AesActive` was changed from `TRUE` to `FALSE` using a Scapy/Pylogix script.

These findings showed vulnerabilities in both the **Network Surface** and **Control Surface**. The **Network Surface** did not provide strong confidentiality or integrity protection, meaning PLC traffic could be observed or manipulated during MITM testing. The **Control Surface** allowed runtime manipulation without proper authentication or access control, meaning unauthorized write actions could affect PLC behavior.

The project also identified the **Software/Firmware Surface** as a potential risk area. Connected Components Workbench was treated as a trusted communication path to the PLC, meaning that if the software were compromised, an attacker could potentially communicate with the PLC through a trusted channel. This creates risk for unauthorized PLC program modification or update denial-of-service scenarios.

The project outcomes supported the need for stronger PLC protections, including firewall/ACL rules, VLAN segmentation, static ARP assignment, Dynamic ARP Inspection, software/firmware integrity checks, and IDS/IPS monitoring. These controls help restrict PLC communication to trusted devices, isolate unauthorized hosts, detect abnormal PLC traffic, identify unauthorized access attempts, block malicious traffic, and reduce the risk of MITM attacks or command injection.

By the end of the project, all major goals were completed:

- Adapted a similar testing environment that replicated the Disney-provided production environment
- Conducted a deep dive into PLC protocols and use cases
- Formulated a scalable security posture for PLC security

