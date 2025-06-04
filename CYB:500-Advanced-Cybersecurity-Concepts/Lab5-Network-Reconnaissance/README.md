# Performing Reconnaissance on a Network

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to perform reconnaissance on a network to test potential vulnerabilities and gather information about hosts and services.

## Tools Used  
- nmap (Network Mapper)

## Procedure  
- Launch nmap to check available options:  
  ```bash
  nmap
- Perform a ping scan to discover active hosts in a subnet:
  ```bash
  nmap -sn 10.0.0.1/24
- Run an OS detection scan with verbose output on a specific target:
  ```bash
  nmap -O -v 10.0.0.1
  
## Results
- Successfully scanned the network to identify live hosts and determine the operating system of a target.
- Reconnaissance was completed to assist in understanding potential vulnerabilities and host characteristics.

## Lessons Learned
- Reconnaissance is a critical early phase in ethical hacking and penetration testing.
- Understanding your network’s exposure helps identify misconfigurations and possible security risks.
