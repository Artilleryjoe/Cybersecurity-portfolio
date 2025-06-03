# Using nslookup for Passive Reconnaissance

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to use `nslookup` for passive reconnaissance to identify IP addresses or Mail Exchange (MX) records associated with a domain.

## Tools Used  
- nslookup

## Procedure  

- Utilize nslookup for passive DNS reconaissance.
  ```bash
  nslookup www.example.com

## Results
- Successfully queried DNS records using nslookup.
- Identified IP address associated with the domain.
- Retrieved mail exchange (MX) records when applicable.
## Lessons Learned
- nslookup is a simple yet powerful tool for passive DNS reconnaissance.
- Querying for MX records can reveal email infrastructure and potential targets.
- Passive techniques like nslookup do not interact directly with the target system, reducing     the risk of detection.
