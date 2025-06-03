# Using the iptables Command to Create a Personal Firewall in Linux

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to use the `iptables` command to create packet-filtering rules and manage network traffic on a Linux system.

## Tools Used  
- iptables command-line utility  
- Linux network interface (ens192 in this case)

## Procedure  
- Verified installation of iptables:
  ```bash
  sudo dpkg -l | grep iptab
- Checked IP address of network interfaces:
  ```bash
  sudo ip addr
- Flushed existing iptables rules:
  ```bash
  sudo iptables -F
- Tested network connectivity by pinging target IP (192.168.1.243).
- Inserted a rule to drop all ICMP packets on interface 'ens192':
  ```bash
  sudo iptables -I INPUT -i ens192 -p icmp -s 0/0 -d 0/0 -j DROP
- Inserted a logging rule for ICMP packets on the same interface:
  ```bash
  sudo iptables -I INPUT -i ens192 -p icmp -s 0/0 -d 0/0 -j LOG
- Tested ping again to confirm ICMP packets were blocked.
- Displayed current iptables rules with line numbers:
  ```bash
  sudo iptables --line-numbers -nL
- Saved current rules to a file:
  ```bash
  sudo iptables-save > iptablesrules.txt
- Viewed saved rules:
  ```bash
  sudo less iptablesrules.txt
- Flushed rules to clear firewall:
  ```bash
  sudo iptables -F
- Tested ping again to confirm connectivity was restored.
- Restored rules from saved file:
  ```bash
   sudo iptables-restore < iptablesrules.txt

  ## Results
  - Successfully created a firewall that blocks ICMP traffic on interface ens192
  - Verified packet filtering by ping tests before and after rule insertion.
  - Demonstrated saving and restoring firewall rules using iptables-save and iptables-restore
    
  ## Lessons Learned
  - iptables provides granular control over packet filtering on Linux systems.
  - Dropping and logging packets helps monitor and control network traffic.
  - Saving and restoring rules ensures persistence and ease of management.
  - Testing connectivity at each step is crucial to verify firewall behavior.
