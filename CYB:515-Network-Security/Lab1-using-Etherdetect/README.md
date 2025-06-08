# Using EtherDetect for Packet Analysis

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use EtherDetect to capture and analyze network packets in a Windows environment. The goal is to observe how network protocols transmit data and how sensitive information may be exposed over unsecured connections.

## Tools Used  
- EtherDetect Packet Sniffer (Windows)  
- Windows 10 virtual machine  
- Local or test network with browser traffic

## Procedure  

- Download and install EtherDetect on a Windows VM

- Launch the tool with administrative privileges

- Select the appropriate network adapter for monitoring

- Start a capture session

- On the same machine or another VM on the network:
  - Open a web browser and visit an unencrypted (HTTP) site or send test traffic via Netcat

- Observe the packet stream in EtherDetect:
  - Identify source and destination IPs
  - Filter by protocol (e.g., HTTP, FTP, SMTP)
  - Look for exposed usernames, passwords, or form data in plaintext

- Stop the capture and review the session log:
  - Save or export results if needed

## Results  
- EtherDetect successfully captured network traffic on the monitored interface  
- HTTP traffic showed visible GET/POST data including URL parameters  
- DNS queries and TCP handshakes were visible in real time  
- No encrypted content (HTTPS) could be parsed, reinforcing its importance

## Lessons Learned  
- Packet sniffers like EtherDetect illustrate the risks of plaintext transmission  
- Encrypted protocols (HTTPS, SSH) are essential to protect against passive monitoring  
- Traffic inspection tools are valuable for both attacker simulations and blue team visibility  
- Ethical packet analysis helps inform secure system and network design
