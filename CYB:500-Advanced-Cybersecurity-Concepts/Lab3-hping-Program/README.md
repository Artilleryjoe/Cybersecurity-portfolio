# Using the `hping` Program

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to use the `hping3` program to send SYN packets to a target system, which can be used to test network connectivity and perform basic port scanning.

## Tools Used  
- `hping3` command-line tool  
- Linux terminal environment

## Procedure  
- Launch a terminal in Kali Linux.  
- Use the `hping3` tool to send 4 SYN packets to port 80 of a target host:
  ```bash
  hping3 -c 4 -p 80 192.168.122.7
  ```

## Results  
- Successfully sent 4 SYN packets to the target.  
- Received replies from the target system, indicating that port 80 is open and responding.

## Lessons Learned  
- `hping3` is a powerful utility for crafting custom network packets.  
- It is commonly used for firewall testing, port scanning, and network reconnaissance.  
- Understanding how SYN packets operate is crucial for detecting and defending against SYN-based attacks such as SYN floods.

