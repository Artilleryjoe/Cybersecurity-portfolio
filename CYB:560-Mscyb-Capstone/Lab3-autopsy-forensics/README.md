# Analyzing Forensics with Autopsy

## Course  
CYB/560 – MS Cybersecurity Capstone

## Objective  
This lab demonstrates how to use Autopsy, a digital forensics platform, to analyze evidence from a disk image. The goal is to extract artifacts such as user activity, deleted files, browser history, and potential indicators of compromise in a structured forensic investigation.

## Tools Used  
- Autopsy (latest version)  
- Disk image file (.E01, .img, or .dd format)  
- Host system with administrative privileges  
- Internet access (optional for plugin updates)

## Procedure  
- Launch Autopsy and create a new case  
- Import the provided disk image as a data source  
- Enable ingest modules:
  - Recent Activity
  - File Type Identification
  - Hash Lookup
  - Web Artifacts
  - Keyword Search  
- Allow the modules to process the image (may take several minutes)  
- Navigate through the following artifact sections:
  - Web History: Check visited URLs and downloads  
  - Deleted Files: Recover files flagged as deleted  
  - User Activity: Review logins, USB usage, and program execution  
  - Keyword Hits: Search for suspicious terms or file names  
- Export findings and generate a report for documentation

## Results  
- Identified a user account with elevated privileges that accessed unauthorized content  
- Recovered deleted documents tied to sensitive project data  
- Detected installation of a known remote access trojan based on file signature and path  
- Browser history showed visits to suspicious domains and use of anonymizing tools

## Lessons Learned  
- Autopsy provides a powerful GUI-driven method for forensic analysis of storage media  
- Ingest modules automate much of the evidence triage, but manual review remains critical  
- Time-stamped activity logs and metadata are essential for establishing timelines  
- Forensics must be conducted with integrity to ensure admissibility in legal or organizational proceedings
