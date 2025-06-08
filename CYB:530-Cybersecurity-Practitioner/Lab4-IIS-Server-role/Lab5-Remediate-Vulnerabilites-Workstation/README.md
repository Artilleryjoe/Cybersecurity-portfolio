# Remediating Vulnerabilities on the Local Workstation

## Course  
CYB/530 – Cybersecurity Practitioner

## Objective  
This lab demonstrates how to identify and remediate vulnerabilities on a local Windows workstation using built-in tools and manual remediation steps. The goal is to reduce exposure to known threats and align the workstation with baseline security standards.

## Tools Used  
- Windows 10 or 11  
- Microsoft Defender Security Center  
- Windows Update  
- Local Group Policy Editor  
- Optional: MBSA, Nessus Essentials, or Qualys agent (if available)

## Procedure  

- **Initial Assessment:**
  - Check system update status:
    ```powershell
    Get-WindowsUpdateLog
    ```
  - Open **Windows Security** > **Device Security** > **Core Isolation** and **Memory Integrity**
  - Review **Virus & threat protection** status and update definitions

- **Apply Security Patches:**
  - Run Windows Update:
    ```powershell
    Install-WindowsUpdate
    ```
  - Confirm cumulative updates and security patches are installed

- **Harden System Settings:**
  - Open **Local Group Policy Editor** and review:
    - Password policy (complexity, lockout, expiration)  
    - Account lockout threshold  
    - UAC settings

- **Audit Installed Applications:**
  - Remove untrusted or outdated software  
  - Update vulnerable applications like Java, Adobe Reader, etc.

- **Optional Third-Party Scan:**
  - If using MBSA or Nessus, perform a local vulnerability scan  
  - Review CVE references and apply mitigation based on scan results

## Results  
- All pending system updates and security patches were successfully installed  
- Unused or potentially vulnerable applications were removed  
- Local policies were updated to meet minimum security standards  
- No critical vulnerabilities remained after remediation steps  
- Optional scan (if used) confirmed a clean or significantly reduced risk state

## Lessons Learned  
- Vulnerability remediation is an ongoing process, not a one-time event  
- Built-in Windows tools offer powerful protection if regularly maintained  
- Policy enforcement plays a major role in local security posture  
- Removing unnecessary software reduces attack surface significantly  
- Automated tools like Nessus can help validate manual efforts and identify missed risks
