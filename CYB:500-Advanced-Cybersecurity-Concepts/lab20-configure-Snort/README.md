# Lab 20: Configuring Snort for Network Intrusion Detection

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to configure Snort as a network intrusion detection system (NIDS), including basic rule creation and alert testing to monitor for suspicious traffic on a local network.

## Tools Used  
- Snort (open-source NIDS)  
- Linux (Ubuntu or Kali)  
- Terminal  
- Network interface in promiscuous mode  
- Custom Snort rules

## Procedure  
- Update package sources and install Snort:
  ```bash
  sudo apt update
  sudo apt install snort
- Identify your active network interface:
  ```bash
  ip a
- Configure the interface in Snort config
    - Edit ```/etc/snort/snort.conf``` to specify your HOME_NET
      Example:
      var HOME_NET 192.168.1.0/24
- Create a custom rule file:
  ```bash
  sudo nano /etc/snort/rules/local.rules
- Add a simple rule (e.g.,ICMP alert)
  ```alert icmp any any -> any any (msg:"ICMP Packet Detected"; sid:1000001; rev:1;)
- Include the rule file in ```snort.conf```:
  ```bash
  include $RULE_PATH/local.rules
- Start Snort in IDS mode:
  ```bash
  sudo snort -A console -q -c /etc/snort/snort.conf -i -eth0(replace with your interface)
- Test the rule by sending a ping:
  ```bash
  ping -c 1 8.8.8.8

## Results
- Snort successfully installed and configured
- Custom rule triggered on ICMP traffic
- Alert message printed to console:
  ```css
  [**] [1:1000001:1] ICMP Packet Detected [**]
- Demonstrated live detection of network activity based on custom rules

## Lessons Learned
- Snort is a powerful and flexible open-source IDS
- Custom rules allow detection of specific types of traffic
- Proper configuration of snort.conf and rule paths is essential
- Snort can be used to monitor real-time traffic or review logs post-event
