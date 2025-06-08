# Remediating Vulnerabilities on the Network

## Course  
CYB/530 – Cybersecurity Practitioner

## Objective  
This lab demonstrates how to identify and remediate vulnerabilities across a network environment. The goal is to strengthen overall security posture by addressing misconfigurations, outdated services, and exploitable weaknesses identified through scanning and manual inspection.

## Tools Used  
- Nessus Essentials or OpenVAS (Greenbone)  
- Nmap  
- Remote access tools (e.g., RDP, SSH, or Group Policy)  
- Windows Server and/or Linux systems  
- Optional: Patch management platform (WSUS, Ansible, etc.)

## Procedure  

- **Network Discovery:**
  - Use Nmap to identify live hosts and open services:
    ```bash
    nmap -sS -p- 192.168.1.0/24
    ```

- **Vulnerability Scanning:**
  - Launch a scan using Nessus or OpenVAS targeting discovered hosts  
  - Document vulnerabilities with CVSS scores and affected services

- **Prioritize Remediation:**
  - Focus on vulnerabilities with:
    - CVSS score ≥ 7.0  
    - Known public exploits  
    - Direct exposure to the internet or internal critical systems

- **Remediate Findings:**
  - Apply security patches and firmware updates to affected devices  
  - Disable or reconfigure insecure services (e.g., SMBv1, Telnet, outdated SSL)  
  - Harden system configurations (e.g., enforce strong authentication, update firewall rules)  
  - Remove unnecessary open ports or protocols

- **Validate Remediation:**
  - Rescan the network with the same tool  
  - Confirm previously flagged vulnerabilities have been addressed

## Results  
- Successfully scanned a small network of 4 systems  
- Identified multiple medium and high-severity vulnerabilities  
  - Example: Outdated Apache server with known CVE  
  - Example: Windows Server with SMBv1 enabled  
- Applied updates, disabled legacy protocols, and reconfigured services  
- Follow-up scans showed all high-severity vulnerabilities resolved  
- Documented change control and compliance records

## Lessons Learned  
- Network-wide remediation requires coordination, prioritization, and repeatable workflows  
- Vulnerability scanners provide insight, but remediation still requires expert judgment  
- Disabling legacy services and patching consistently are top defenses against real-world attacks  
- Validation scans are essential to confirm remediation efforts were successful  
- Documentation supports audit readiness and improves institutional knowledge
