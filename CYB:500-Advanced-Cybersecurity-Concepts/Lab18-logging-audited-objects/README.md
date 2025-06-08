
# Lab 18: Enabling Logging for Audited Objects

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to enable logging for audited objects on a Windows system using the Local Security Policy, which is essential for tracking access to sensitive files, folders, and registry keys.

## Tools Used  
- Windows OS  
- Local Security Policy (`secpol.msc`)  
- Event Viewer  
- Windows File Explorer (for test object access)

## Procedure  
- Open the **Local Security Policy**:
  - Press `Win + R`, type `secpol.msc`, and press Enter
- Navigate to:  
  `Local Policies` > `Audit Policy`
- Enable the following policy settings:
  - **Audit object access**: Set to "Success" and/or "Failure"
- Apply the settings and close the policy window
- Identify a test file or folder (e.g., `C:\AuditTest`)
- Right-click the object > **Properties** > **Security** tab > **Advanced** > **Auditing**
- Add a new auditing entry:
  - Choose "Everyone" or a specific user
  - Select "Success" and/or "Failure" for desired access types (e.g., Read, Write)
- Access the object (read or modify) to generate an audit event
- Open **Event Viewer**:
  - Navigate to `Windows Logs` > `Security`
  - Look for Event ID 4663 (An attempt was made to access an object)

## Results  
- Audit policy was successfully configured via Local Security Policy  
- A test folder was monitored for access events  
- Accessing the folder generated a log entry in the Security event log  
- Event Viewer showed the audited activity under Event ID 4663

## Lessons Learned  
- Auditing object access is crucial for tracking unauthorized activity on sensitive files or system resources  
- Proper configuration requires both enabling audit policies and setting specific object-level audit entries  
- Audit logs can generate a lot of noise; it's important to fine-tune based on critical assets  
- Security event logs provide detailed, time-stamped records for forensic and compliance purposes
