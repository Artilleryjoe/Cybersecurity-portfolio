# Performing ARP Poisoning with Wireshark Monitoring

## Course  
CYB/550 – Technical Enterprise Security

## Objective  
This lab demonstrates how to carry out an Address Resolution Protocol (ARP) poisoning attack to intercept traffic between two devices on a local network. Wireshark is used to verify the success of the attack and inspect captured packets.

## Tools Used  
- Kali Linux  
- arpspoof or ettercap  
- Wireshark  
- Two target virtual machines (or devices on LAN)

## Procedure  
- Enable IP forwarding on the attacker machine:
  ```bash
  echo 1 > /proc/sys/net/ipv4/ip_forward
- Identify the IP addresses of the target and the default gateway using arp -a or ip route
- Start Wireshark to monitor network traffic on the attack interface
- Launch ARP poisoning attack using:
    ```bash
    arpspoof -i eth0 -t [target IP] [gateway IP]
    arpspoof -i eth0 -t [gateway IP] [target IP]
- Monitor in Wireshark for captured packets between victim and gateway
- Look for intercepted HTTP data, credentials, or unencrypted sessions

## Results
- Target device updated its ARP cache with attacker MAC address
- All traffic between target and gateway flowed through the attacker
- Wireshark captured credentials sent over unsecured HTTP
- Confirmed successful MITM position via packet inspection

## Lessons Learned
- ARP spoofing is a fundamental attack vector on local networks without authentication
- Defense mechanisms include:
   - Static ARP entries
   - Dynamic ARP Inspection (DAI) on managed switches
   - Encryption protocols (HTTPS, SSH) to prevent data leakage even if intercepted
- Detection tools such as ARPWatch and IDS signatures can identify anomalies in ARP tables
