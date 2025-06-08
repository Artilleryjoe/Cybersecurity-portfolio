# Using Microsoft Baseline Security Analyzer (MBSA)

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use Microsoft Baseline Security Analyzer (MBSA) to assess the security configuration of a Windows system. MBSA scans for missing patches, weak account settings, and system misconfigurations based on Microsoft's security baselines.

## Tools Used  
- Microsoft Baseline Security Analyzer (MBSA)  
- Windows 10 or 7 test system  
- Administrator access  
- Internet connection (for update checks)

## Procedure  

- Download and install MBSA from the Microsoft archive (legacy tool)

- Launch MBSA with administrator rights

- Select scan type:
  - Choose "Scan a computer" or "Scan multiple computers" if working on a domain
  - Input IP address or system name

- Configure scan options:
  - Include Windows Update checks
  - Check for administrative vulnerabilities
  - Scan for weak passwords, firewall status, and more

- Start the scan and allow it to complete

- Review the results:
  - Missing security updates
  - Insecure configurations
  - User account vulnerabilities
  - Service configurations (e.g., unnecessary ports)

## Results  
- MBSA successfully scanned the test Windows system  
- Identified multiple missing security updates and configuration issues  
- Report included password policy weaknesses, unused accounts, and file share settings  
- Exported results to HTML for documentation and review

## Lessons Learned  
- MBSA provides a fast, graphical overview of Windows security posture  
- Despite being a legacy tool, it demonstrates key vulnerability assessment concepts  
- Regular configuration reviews are critical to reduce internal attack surfaces  
- More modern tools (e.g., Microsoft Defender for Endpoint, SCCM, or PowerShell scripts) should now be used in enterprise environments
