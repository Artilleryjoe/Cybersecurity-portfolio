# Lab 6: Performing a MITM Attack

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to configure tools for a successful Man-in-the-Middle (MITM) attack using ARP spoofing and packet capture techniques.

## Tools Used  
- Wireshark  
- tcpdump  
- arpspoof  
- VirtualBox lab setup with Ubuntu, Windows 10, and Base VM

## Procedure  
- Connect to Base VM, Ubuntu VM, and Windows 10 VM
- On Base VM, open PowerShell and run a continuous ping to the Windows 10 VM (ping 192.168.1.241 -t)
- On Ubuntu, open Terminal and run ARP spoofing to impersonate the Base VM:
  ```sudo arpspoof -i ens192 -t 192.168.1.241 192.168.1.240```
- Open a second terminal and run ARP spoofing to impersonate the Windows 10 VM:
  ```sudo arpspoof -i ens192 -t 192.168.1.240 192.168.1.241```
- Enter ```sudo -i``` to elevate privileges
- Enable IP forwarding by running:
  ```echo 1 > /proc/sys/net/ipv4/ip_forward```
- Observe that the ping traffic continues uninterrupted on the Base VM, indicating the MITM attack is successfully intercepting traffic
- Launch tcpdump to capture traffic:
  ```tcpdump -i ens192```
- Open Wireshark on the Base VM to inspect packets from ```192.168.1.241```
- Save the captured packets as ```mitm.pcap```
  
## Results
- ARP spoofing redirects traffic between Base VM and Windows 10 VM through Ubuntu
- IP forwarding on Ubuntu maintains uninterrupted communication
- tcpdump and Wireshark confirm successful packet interception
- Captured packets saved as mitm.pcap for further analysis

## Lessons Learned
- ARP spoofing is a powerful method for conducting MITM attacks on local networks
- IP forwarding is essential for maintaining traffic flow during an interception
- Continuous packet monitoring with tools like Wireshark or tcpdump allows for real-time visibility into network activity
- Proper network segmentation and ARP inspection tools can help defend against these types of attacks in real environments
