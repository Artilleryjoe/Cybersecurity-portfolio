# Installing the Web Server (IIS) Server Role

## Course  
CYB/530 – Cybersecurity Practitioner

## Objective  
This lab demonstrates how to install and configure the Web Server (IIS) role on a Windows Server system. Understanding IIS is foundational for hosting internal web applications and learning how to harden exposed services.

## Tools Used  
- Windows Server 2019 or later  
- Server Manager  
- Optional: PowerShell  
- Web browser for testing

## Procedure  

### Using Server Manager:

- Open **Server Manager**  
- Click on **Manage** > **Add Roles and Features**  
- In the wizard:
  - Choose **Role-based or feature-based installation**  
  - Select the local server  
  - Check the box for **Web Server (IIS)**  
  - Accept defaults or add features as needed  
- Proceed through the wizard and click **Install**  
- Wait for installation to complete and verify success

### Using PowerShell (alternative method):
    ```powershell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
***Verify IIS is running:
- Open a browser and visit:
    ```bash
    HTTP://localhost
- You should see the default IIS landing page

## Results
IIS installed successfully using Server Manager
Verified that the web service was reachable locally via HTTP
Management tools installed enabled configuration of sites, bindings, and security settings
IIS Manager accessible for further web configuration

## Lessons Learned
- IIS is easy to install but must be secured before production use
- The default configuration can expose sensitive version information or allow weak protocols
- Windows Server provides both GUI and PowerShell methods for role management
- Hosting a secure web application requires follow-up steps including HTTPS setup, access control, and service hardening
