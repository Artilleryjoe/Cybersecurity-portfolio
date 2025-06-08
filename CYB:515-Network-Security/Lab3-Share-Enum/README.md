# Using ShareEnum to Enumerate Network Shares

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use ShareEnum, a graphical tool from Sysinternals, to enumerate shared folders across a local Windows network. The goal is to identify open, misconfigured, or overly permissive shares that could expose sensitive data.

## Tools Used  
- ShareEnum (Microsoft Sysinternals Suite)  
- Windows 10 virtual machine (attacker)  
- One or more networked Windows systems (targets)  
- Local network or isolated lab subnet

## Procedure  

- Download ShareEnum from the official Microsoft Sysinternals website

- Launch ShareEnum with administrative privileges on the scanning VM

- Allow the tool to scan the local subnet or specific IP ranges

- Review the list of detected machines and their exposed shares:
  - Check share names, share paths, and access levels (Everyone, Authenticated Users, etc.)

- Highlight any shares that:
  - Are accessible by "Everyone"  
  - Lack password protection  
  - Provide access to sensitive or system folders (e.g., C$, Admin$)

- Attempt to connect to a listed share and open or copy a test file

- Document any inconsistencies between expected and actual share permissions

## Results  
- ShareEnum successfully discovered shared folders across the test network  
- At least one system had a share accessible by the "Everyone" group  
- Shares with open read access allowed retrieval of files without authentication  
- Hidden administrative shares (e.g., `C$`) were visible but access was denied without credentials

## Lessons Learned  
- Share permissions are often misconfigured, especially in unmanaged networks  
- Default or overly permissive access can expose sensitive data to lateral movement  
- Enumeration tools like ShareEnum help identify risks that may go unnoticed by users or sysadmins  
- Regular auditing of shared resources is essential for enterprise security hygiene
