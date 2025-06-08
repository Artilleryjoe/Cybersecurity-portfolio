# Lab 25: Detecting a Rootkit

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to detect potential rootkits on a Linux system using command-line tools such as `chkrootkit` and `rkhunter`. Rootkits are stealthy types of malware designed to gain unauthorized root access while avoiding detection.

## Tools Used  
- chkrootkit  
- rkhunter (Rootkit Hunter)  
- Linux terminal  
- System log inspection (`/var/log/`, `dmesg`)  

## Procedure  

### Using chkrootkit
- Install chkrootkit:
  ```bash
  sudo apt update
  sudo apt install chkrootkit
- Run a full scan:
  ```bash
  sudo chkrootkit
***Using rkhunter***
  - install rkhunter:
    ```bash
    sudo apt install rkhunter
  - Update rootkit database:
    ```bash
    sudo rkhunter --update
  - Run a scan:
    ```bash
    sudo rkhunter --check
  ***Manual Inspection***
  - Check for network listeners:
    ```bash
    netstat -tulnp
  - Search for hidden processes:
    ```bash
    ps -ef | grep -i hidden
  - Inspect system logs:
    ```bash
    less /var/log/auth.log
    dmesg | grep -i rootkit
    
## Results
- chkrootkit scan completed with no known rootkits detected
- rkhunter flagged a few warnings (e.g., hidden files, modified binaries) that were verified as false positives
- Manual inspection of logs and network connections revealed no anomalies
- System confirmed clean, or issues identified and remediated

## Lessons Learned
- Rootkits are difficult to detect due to their ability to hide in plain sight
- Regular scans with tools like chkrootkit and rkhunter are essential for proactive security
- False positives are common and should be cross-checked with file hashes and logs
- Kernel-level rootkits may require offline or forensic inspection to fully remove
- Defense-in-depth strategies and integrity monitoring (e.g., Tripwire, AIDE) can help detect tampering early
