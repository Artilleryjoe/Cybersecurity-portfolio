# Identifying Search Options in Metasploit

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to identify and utilize search options in Metasploit to locate specific modules and vulnerabilities.

## Tools Used  
- Metasploit Framework  
- PostgreSQL Database

## Procedure  
- Start the PostgreSQL service required by Metasploit
```bash
service postgresql start

- Initialize the Metasploit database
msfdb init

- Launch Metasploit console and display search help
msfconsole
search -h

- Search for a specific CVE within Metasploit
search CVE-2013-2465
