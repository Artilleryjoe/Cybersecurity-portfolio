# Using eLiteWrap to Package an Executable

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use eLiteWrap to package a Windows executable with custom options such as password protection, embedded resources, and silent execution. The purpose is to understand how software packaging tools can be used both for legitimate software deployment and for obfuscation by attackers.

**Disclaimer:** This lab was performed in a controlled test environment. No malicious or unauthorized software was created or distributed.

## Tools Used  
- eLiteWrap (Windows executable wrapper)  
- Windows 10 virtual machine  
- Custom test `.exe` (e.g., a basic compiled C program or test script)

## Procedure  

- Download and install eLiteWrap from a trusted source

- Launch eLiteWrap GUI and create a new project

- Select the target `.exe` file (e.g., a harmless test program compiled from C or PowerShell)

- Configure options such as:
  - Output file name and icon  
  - Add password protection (optional)  
  - Set silent execution or hide console window  
  - Bind additional files (e.g., a .txt or DLL dependency)

- Generate the wrapped executable:
  - Click "Build" and save the final output

- Test the wrapped executable by running it:
  - If a password was set, confirm prompt behavior  
  - If silent, verify execution via Task Manager or logs

- (Optional) Upload both original and wrapped executables to VirusTotal to analyze detection rates

## Results  
- eLiteWrap successfully created a wrapped `.exe` file with selected configuration options  
- Password protection prompt appeared as expected (if enabled)  
- File executed silently when configured to suppress the console window  
- VirusTotal results showed increased detection for the wrapped version (depending on AV engines)

## Lessons Learned  
- Tools like eLiteWrap are often used for benign deployment but can also hide payloads  
- Wrapping executables may bypass basic user defenses or confuse non-technical users  
- Awareness of executable packaging techniques is critical for blue teams and malware analysts  
- Static analysis and sandbox testing are necessary when encountering wrapped executables in the wild
