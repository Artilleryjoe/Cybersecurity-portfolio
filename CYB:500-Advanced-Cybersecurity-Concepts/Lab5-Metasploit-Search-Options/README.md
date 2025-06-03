# Identifying Search Options in Metasploit

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to identify and utilize search options in Metasploit to locate specific modules and vulnerabilities.

## Tools Used  
- Metasploit Framework  
- PostgreSQL Database

## Procedure  
- Start the PostgreSQL service required by Metasploit:
- ```bash
  service postgresql start
- Initialize the Metasploit database:
  ```bash
  msfdb init
- Launch Metasploit console and display search help:
  ```bash
  msfconsole
- Then inside the msf console prompt:
  ```bash
  search -h
- Search for a specfic CVE within Metasploit:
  ```bash
  search CVE-2013-2465

## Results
- Successfully initialized Metasploit and its supporting database.
- Executed a search for modules referencing CVE-2013-2465.
- Observed the output detailing matching exploits or auxiliary modules available.
## Lessons Learned
- Metasploit's built-in search functionality allows for precise module discovery based on keywords, CVEs, authors, platforms, and more.
- Searching by CVE is a practical method for verifying whether a vulnerability is exploitable using known modules.
- Understanding how to initialize and interface with Metasploit's database backend is essential for effective vulnerability research.

