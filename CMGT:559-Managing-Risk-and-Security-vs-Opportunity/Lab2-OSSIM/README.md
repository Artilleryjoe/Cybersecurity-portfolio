# Performing Vulnerability Scan Using OSSIM

## Course  
CMGT/559 – Managing Risk and Security vs. Opportunity

## Objective  
This lab demonstrates how to use OSSIM (Open Source Security Information Management) to perform a vulnerability scan across a networked environment. The goal is to identify security weaknesses, assess exposure risk, and generate actionable intelligence to support informed mitigation strategies.

## Tools Used  
- OSSIM by AlienVault (Community Edition)  
- Web-based OSSIM Management Console  
- Target VM or physical host with known vulnerabilities  
- Optional: Credentialed scan configuration

## Procedure  

- Log into the OSSIM web console with administrative credentials

- Navigate to the **Vulnerabilities** section and create a new scan job:
  - Target: IP address or range of the test network  
  - Scan type: Full and fast  
  - Optionally provide system credentials for deeper detection

- Launch the scan and monitor progress through the OSSIM dashboard

- Upon completion, review the vulnerability report:
  - Vulnerability title and CVE ID  
  - Severity (High, Medium, Low)  
  - Affected services and operating systems  
  - Suggested remediations or references

- Export report for documentation or risk analysis

## Results  
- OSSIM identified multiple vulnerabilities on the target host, including outdated OpenSSH and weak SMB configurations  
- Report provided CVSS scores and cross-referenced known CVEs  
- No false positives observed in the environment  
- Follow-up actions included patching OpenSSH and disabling unused services

## Lessons Learned  
- OSSIM provides a centralized platform for vulnerability scanning, threat detection, and event correlation  
- Regular scans help identify risk early and prioritize remediation before exploitation  
- Integration with SIEM and asset tracking makes OSSIM valuable for ongoing risk management  
- Vulnerability management must be continuous, not reactive — especially in dynamic enterprise networks
