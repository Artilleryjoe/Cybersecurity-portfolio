# Demonstrating Mapping and Quarantining a Vulnerable System

## Course  
CMGT/559 – Managing Risk and Security vs. Opportunity

## Objective  
This lab demonstrates how to identify a vulnerable host within a network, map its connections, and isolate it using basic containment techniques. The goal is to understand how quarantine actions reduce risk while maintaining operational integrity in enterprise environments.

## Tools Used  
- Network scanning utility (e.g., Nmap, Angry IP Scanner)  
- Virtualized test network (Hyper-V, VirtualBox, or GNS3)  
- Host firewall settings or VLAN segmentation tools  
- Optional: OSSIM or SIEM logs for threat correlation

## Procedure  
- Begin with a live network scan to identify all connected devices:
    ```bash
    nmap -sP 192.168.1.0/24
- Identify a vulnerable or misconfigured system (e.g., outdated software, open RDP port):
    ```bash
    nmap -sV -p- 192.168.1.105
- Document all open ports and detected services
- Trace network dependencies or connected systems using traceroute or similar:
    ```bash
    traceroute 192.168.1.105
- Quarantine the vulnerable system by:

- Moving it to a separate VLAN or

- Blocking inbound/outbound traffic using host firewall rules or router ACLs

- Verify containment:

- Confirm the system cannot reach sensitive segments

Log restricted traffic attempts via firewall or SIEM alerts

## Results
- Successfully detected a vulnerable host running outdated SMB services
- Mapped its connection to internal file shares and external IPs
- Isolated the system from the main LAN using a dedicated VLAN
- SIEM logs confirmed the device was no longer sending unfiltered traffic post-containment

## Lessons Learned
- Network mapping is essential for understanding risk exposure in real time
- Containment strategies must be fast, targeted, and minimally disruptive
- Quarantining is a critical short-term mitigation measure prior to patching or reimaging
- Effective quarantine relies on layered visibility tools and access control at multiple levels
