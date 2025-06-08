# Installing the Failover Cluster Feature

## Course  
CYB/540 – Cryptography

## Objective  
This lab demonstrates how to install the Failover Clustering feature in Windows Server to prepare for high-availability configurations. While not cryptographic in nature, this task supports secure, fault-tolerant infrastructure essential to enterprise security.

## Tools Used  
- Windows Server 2019 or later  
- Server Manager  
- PowerShell (optional)  
- Administrative privileges  

## Procedure  

### Using Server Manager
- Open **Server Manager** on the Windows Server machine  
- Navigate to **Manage > Add Roles and Features**  
- Proceed through the wizard to the **Features** section  
- Select **Failover Clustering**  
- Complete the installation and reboot if prompted  

### Using PowerShell (alternative)
- Open PowerShell as Administrator  
- Run the following command:
    ```powershell
    Install-WindowsFeature -Name Failover-Clustering -IncludeManagementTools
- Confirm installation status with:
    ```powershell
    Get-WindowsFeature Failover-Clustering
## Results
- The Failover Clustering feature installs successfully through either method
- The system is now prepared for creating and managing high-availability clusters
- The feature appears under installed features and management tools in Server Manager

## Lessons Learned
- High-availability clustering enhances system resilience and uptime
- Installing cluster features requires administrative privileges
- Even infrastructure-level features contribute to security by reducing failure risks
- PowerShell provides an efficient and scriptable alternative to GUI-based installation
