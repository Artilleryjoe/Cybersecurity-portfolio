# Performing a DHCP Starvation Attack

## Course  
CYB/560 – MS Cybersecurity Capstone

## Objective  
This lab demonstrates how to simulate a DHCP starvation attack to test the resilience of a network’s DHCP service. The goal is to understand how attackers exhaust IP address pools to disrupt network connectivity or pave the way for rogue DHCP servers.

## Tools Used  
- Kali Linux or penetration testing VM  
- `yersinia` or `dhcpstarv` tool  
- DHCP-enabled network or lab environment  
- Wireshark (optional for packet observation)

## Procedure  
- Launch Kali Linux and open a terminal  
- Install `yersinia` (if not already installed):
    ```bash
    sudo apt install yersinia
- Start yersinia in interactive mode:
    ```bash
    sudo yersinia -I
- Navigate to the DHCP module and select the DHCP DISCOVER flood option
(Alternatively, use a command-line script like dhcpstarv.py to send multiple DHCP requests)
- Monitor DHCP traffic using Wireshark:
    ```bash
    sudo wireshark
  - Filter: bootp
- Observe as the legitimate DHCP server becomes overwhelmed, exhausting its IP address pool
- Attempt to connect a new client to confirm failure in obtaining an IP address

## Results
- Successfully flooded the DHCP server with spoofed DISCOVER requests
- Exhausted the available IP pool, denying new clients access to the network
- Validated the vulnerability of unauthenticated DHCP environments
- Demonstrated potential for rogue DHCP server insertion following starvation

## Lessons Learned
- DHCP starvation attacks exploit the lack of authentication in DHCP
- Mitigations include port security, DHCP snooping, MAC address limits, and static IP allocations for critical systems
- Testing this attack in a controlled lab is crucial to avoid disrupting production networks
- Detection tools like IDS/IPS and anomaly-based monitoring can alert admins to abnormal DHCP traffic
