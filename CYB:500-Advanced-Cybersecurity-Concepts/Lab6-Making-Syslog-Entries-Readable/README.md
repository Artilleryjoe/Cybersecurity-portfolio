# Making Syslog Entries Readable

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to make Syslog entries more human-readable by parsing and extracting meaningful fields from system log files.

## Tools Used  
- Command Line Interface (CLI)  
- `cut` command  
- `/var/log/syslog` file

## Procedure  

- Navigate to the system log directory:
  ```bash
  cd /var/log
- List the contents of the directory to locate the syslog file:
    ```bash
    ls
- Extract the first 20 characters of each line in the syslog (timestamp/hostname):
    ```bash
    cut -c21-60 syslog
- Split each line using colon : as a delimiter and print the first three fields:
  ```bash
  cut -d ":" -f1-3 syslog

## Results
- Successfully viewed and parsed syslog entries using cut.
- Gained structured visibility into log file content such as timestamps, processes, and message segments.
## Lessons Learned
- System logs can be easily parsed using basic Linux tools like cut to isolate specific fields.
- Reading log files in segments makes it easier to identify patterns, timestamps, and sources of events.
- This technique supports passive footprinting and can assist in forensic investigations by clarifying raw log data.
