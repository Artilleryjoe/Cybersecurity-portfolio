# Installing and Configuring Active Directory Domain Services (AD DS)

## Course  
CYB/555 – Cybersecurity Architecture

## Objective  
This lab demonstrates how to install and configure Active Directory Domain Services (AD DS) on a Windows Server system. AD DS provides centralized authentication, access control, and directory-based identity services essential to enterprise security architecture.

## Tools Used  
- Windows Server 2019 or 2022  
- Server Manager  
- PowerShell  
- Domain Administrator account

## Procedure  
- Launch **Server Manager** and select **“Add Roles and Features”**  
- Choose **Role-Based or Feature-Based Installation**  
- Select the local server and enable **Active Directory Domain Services**  
- Allow installation of supporting features (DNS, Group Policy Management)  
- Complete installation and reboot if prompted  
- Promote the server to a Domain Controller:  
  - Select **“Add a new forest”**  
  - Define root domain (e.g., `sicherheitsschaf.local`)  
  - Configure Directory Services Restore Mode (DSRM) password  
- Validate installation with:
  ```powershell
  Get-WindowsFeature AD-Domain-Services
and check domain health with:

powershell
Copy
Edit
dcdiag
Results
AD DS successfully installed and server promoted to Domain Controller

Domain structure initialized with forest root: sicherheitsschaf.local

DNS integration and Group Policy Management verified

Initial organizational units and user accounts created

Lessons Learned
Active Directory is a foundational component in enterprise identity and access management (IAM)

Proper planning of domain structure and naming conventions is essential for scalability

Misconfigurations can result in privilege escalation, replication issues, or authentication failures

Security best practices include:

Tiered administration model

Audit policies and logging

Regular backup and restore validation
