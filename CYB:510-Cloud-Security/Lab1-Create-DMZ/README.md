# Creating a Demilitarized Zone (DMZ) Using GNS3 and PuTTY

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to create a virtual DMZ (Demilitarized Zone) environment using GNS3 for network simulation and PuTTY for device access. The DMZ is used to isolate public-facing services from internal networks and practice network segmentation and firewall configuration.

## Tools Used  
- GNS3 (Graphical Network Simulator 3)  
- PuTTY (SSH/Telnet Client)  
- Cisco or Linux-based virtual routers and hosts  
- Firewall image or appliance (e.g., Cisco ASA, pfSense, etc.)

## Procedure  
- Launch GNS3 and create a new project named `DMZ_Simulation`
- Drag the following nodes into the workspace:
  - One internal LAN switch and host
  - One firewall (e.g., pfSense or Cisco ASA)
  - One DMZ switch and public-facing server
  - One external router or simulated internet connection
- Connect nodes to simulate:
  - Inside network → firewall (inside interface)
  - DMZ network → firewall (dmz interface)
  - Outside router → firewall (outside interface)
- Configure IP addressing for each subnet:
  - Inside: 192.168.1.0/24  
  - DMZ: 192.168.2.0/24  
  - Outside: 192.0.2.0/24 (test public IP block)
- Open PuTTY and connect to each device using Telnet or SSH
- Configure the firewall rules:
  - Allow inbound HTTP/HTTPS from outside to DMZ server
  - Allow outbound responses from DMZ to outside
  - Block direct access from outside to inside
- Test:
  - Ping and access web server in DMZ from outside
  - Verify inside network is protected from direct access

## Results  
- GNS3 topology successfully simulated a segmented network with a DMZ  
- PuTTY used to configure and verify firewall and host connectivity  
- Inbound access restricted to DMZ only; inside network remained isolated  
- Verified stateful packet inspection and rule enforcement

## Lessons Learned  
- A DMZ provides an important security layer between external and internal networks  
- GNS3 is a powerful tool for visualizing and testing real-world enterprise architectures  
- Firewall rules must be clearly scoped to avoid overexposing internal assets  
- Secure remote access tools like PuTTY are essential for network configuration and troubleshooting
