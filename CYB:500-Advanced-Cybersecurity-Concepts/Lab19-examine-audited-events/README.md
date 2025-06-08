# Lab 19: Examining Audited Events in Event Viewer

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to examine and interpret audited security events in Event Viewer, with a focus on object access events such as file reads, modifications, or deletions triggered by previous audit policy configuration.

## Tools Used  
- Windows OS  
- Event Viewer (`eventvwr.msc`)  
- Local Security Policy (`secpol.msc`)  
- Previously configured audited object (e.g., a file or folder)

## Procedure  
- Ensure that object auditing is already enabled (see Lab 18)
- Access or modify the monitored object to generate audit events
- Open Event Viewer:
  - Press `Win + R`, type `eventvwr.msc`, and press Enter
- In the left pane, navigate to:  
  `Windows Logs` > `Security`
- Use the **Filter Current Log** option to find relevant events:
  - Look for Event ID `4663` (Object access)
  - Optionally include IDs like `4656` (Handle requested) or `4658` (Handle closed)
- Double-click an event to view detailed information:
  - Subject (user)
  - Object name (file or folder)
  - Access type (Read, Write, Delete)
  - Access result (Success or Failure)

## Results  
- Security audit logs successfully displayed in Event Viewer  
- Event ID 4663 confirmed access attempts on the audited folder  
- Log included time, username, object path, and access type  
- Verified that both successful and failed access attempts were recorded

## Lessons Learned  
- Event Viewer provides detailed logs for auditing and forensic analysis  
- Object access events help identify unauthorized file access  
- Event IDs like 4663 and 4656 are key for object auditing  
- Filtering and understanding audit logs is a vital skill for security monitoring and compliance
