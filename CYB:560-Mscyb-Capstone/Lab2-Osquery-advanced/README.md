# Using osquery for Advanced Incident Response and Threat Hunting

## Course  
CYB/560 – MS Cybersecurity Capstone

## Objective  
This lab demonstrates how to use `osquery` to monitor and investigate endpoint activity for signs of compromise. `osquery` allows incident responders to query system data as if it were a SQL database, making it a powerful tool for threat hunting, live forensic analysis, and anomaly detection.

## Tools Used  
- osqueryi (interactive shell) or osqueryd (daemon)  
- Linux or Windows host system  
- Administrative access  
- Terminal or PowerShell

## Procedure  
- Install osquery on the target machine  
- Launch the interactive shell with:
  ```bash
  osqueryi
Run baseline queries:

sql
Copy
Edit
SELECT * FROM processes WHERE name = 'powershell.exe';
SELECT * FROM logged_in_users;
SELECT * FROM listening_ports;
SELECT * FROM users;
SELECT * FROM kernel_info;
SELECT * FROM file WHERE path LIKE '/etc/shadow';
Create a schedule for periodic queries using a config file (if using osqueryd)

Log and analyze the results for suspicious activity such as:

Unknown users or new admin accounts

Unusual ports open

Unrecognized running processes

Tampered system files

Results
Discovered elevated PowerShell usage on a Linux host — flagged as anomaly

Logged presence of a rogue service mimicking SSH

Used query output to support a deeper investigation via additional forensic tools

Scheduled osqueryd to monitor changes in /etc/passwd and login sessions

Lessons Learned
osquery bridges the gap between security operations and system administration

Real-time endpoint visibility is essential for both proactive threat hunting and incident response

Queries must be tailored to the environment and threat model for maximum value

Automating query scheduling allows for scalable continuous monitoring

yaml
Copy
Edit
