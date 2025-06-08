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
Identify your active network interface:

bash
Copy
Edit
ip a
Configure the interface in Snort config:

Edit /etc/snort/snort.conf to specify your HOME_NET
Example:

nginx
Copy
Edit
var HOME_NET 192.168.1.0/24
Create a custom rule file:

bash
Copy
Edit
sudo nano /etc/snort/rules/local.rules
Add a simple rule (e.g., ICMP alert):

bash
Copy
Edit
alert icmp any any -> any any (msg:"ICMP Packet Detected"; sid:1000001; rev:1;)
Include the rule file in snort.conf:

bash
Copy
Edit
include $RULE_PATH/local.rules
Start Snort in IDS mode:

bash
Copy
Edit
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
(Replace eth0 with your interface)

Test the rule by sending a ping:

bash
Copy
Edit
ping -c 1 8.8.8.8
Results
Snort successfully installed and configured

Custom rule triggered on ICMP traffic

Alert message printed to console:

css
Copy
Edit
[**] [1:1000001:1] ICMP Packet Detected [**]
Demonstrated live detection of network activity based on custom rules

Lessons Learned
Snort is a powerful and flexible open-source IDS

Custom rules allow detection of specific types of traffic

Proper configuration of snort.conf and rule paths is essential

Snort can be used to monitor real-time traffic or review logs post-event

False positives can occur; rules must be tuned to the environment

yaml
Copy
Edit

---

Want to proceed with pushing this as **Lab 20**? I can also help you set up extended Snort logging, packet captures, or integration with tools like `barnyard2` or `pulledpork` if you're going deeper.






You said:
confirming spoofing with wireshark


ChatGPT said:
Here’s a polished and professional lab write-up for confirming spoofing with Wireshark, ideal for Lab 21 in your CYB/500 sequence:

markdown
Copy
Edit
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
ip

javascript
Copy
Edit
- In a separate terminal window, send spoofed packets using `hping3`:
```bash
sudo hping3 -a 192.168.1.1 -S -p 80 192.168.1.5
(Where -a sets the spoofed IP, and the last IP is the target)
OR use Scapy:

python
Copy
Edit
from scapy.all import *
spoof = IP(src="192.168.1.1", dst="192.168.1.5")/TCP(dport=80, flags="S")
send(spoof)
In Wireshark, identify spoofed packets by checking:

The source IP field (should show spoofed address)

MAC address mismatch (source IP and MAC don’t match ARP table)

No corresponding TCP response (since the spoofed address didn’t initiate a handshake)

Results
Wireshark successfully captured packets with forged source IP addresses

Discrepancy between source MAC and IP confirmed spoofing

TCP three-way handshake failed to complete, validating that the spoofed packets were not part of a legitimate session

Logs showed source IP as a trusted device, demonstrating the risk of trust-based security

Lessons Learned
Wireshark is an essential tool for identifying spoofed traffic

IP spoofing can bypass IP-based ACLs, firewalls, or monitoring systems

Verifying MAC-IP consistency is a key detection method

Spoofed packets rarely complete TCP handshakes, offering a signature for detection

Network defenses should rely on more than IP address filtering — consider stateful inspection and behavior-based rules
