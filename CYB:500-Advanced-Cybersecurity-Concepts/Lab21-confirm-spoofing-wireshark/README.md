# Lab 21: Confirming Spoofing with Wireshark

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to detect and confirm IP spoofing using Wireshark. Spoofing is a technique in which an attacker falsifies the source IP address in packet headers to disguise their identity or mislead monitoring tools.

## Tools Used  
- Wireshark  
- Kali Linux (or equivalent with packet manipulation tools)  
- hping3 or Scapy (for spoofed packet generation)  
- Target system or loopback environment

## Procedure  
- Open Wireshark and begin packet capture on the appropriate interface (e.g., `eth0`)
- Filter for IP traffic:  
- In a separate terminal window, send spoofed packets using `hping3`:
  ```bash
  sudo hping3 -a 192.168.1.1 -S -p 80 192.168.1.5
  (Where -a sets the spoofed IP, and the last IP is the target)
- In Wireshark, identify spoofed packets by checking:
- The source IP field (should show spoofed address)
- MAC address mismatch (source IP and MAC don’t match ARP table)
- No corresponding TCP response (since the spoofed address didn’t initiate a handshake)

## Results
- Wireshark successfully captured packets with forged source IP addresses
- Discrepancy between source MAC and IP confirmed spoofing
- TCP three-way handshake failed to complete, validating that the spoofed packets were not part of a legitimate session
- Logs showed source IP as a trusted device, demonstrating the risk of trust-based security

## Lessons Learned
- Wireshark is an essential tool for identifying spoofed traffic
- IP spoofing can bypass IP-based ACLs, firewalls, or monitoring systems
- Verifying MAC-IP consistency is a key detection method
- Spoofed packets rarely complete TCP handshakes, offering a signature for detection
- Network defenses should rely on more than IP address filtering — consider stateful inspection and behavior-based rules
