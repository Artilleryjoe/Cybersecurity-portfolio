# Attempting a Zone Transfer

## Course  
CYB/555 – Cybersecurity Architecture

## Objective  
This lab demonstrates how to attempt a DNS zone transfer, which can reveal detailed information about a domain's internal structure if improperly configured. The purpose is to understand how misconfigured DNS servers can leak sensitive data and how to defend against such exposures.

## Tools Used  
- `dig` or `nslookup` (Linux command-line tools)  
- Target test domain  
- Kali Linux or any Linux-based terminal

## Procedure  
- Identify the domain to test (e.g., `example.com`)  
- Use `nslookup` or `dig` to find authoritative name servers:
      ```bash
      nslookup -type=ns example.com
- Attempt a zone transfer against each nameserver:
    ```bash
    dig axfr @ns1.example.com example.com
- Observe the output for internal hostnames, IP addresses, or comments

- Repeat for all discovered name servers

## Results
- Query to ns1.example.com failed with “Transfer failed” — zone transfer blocked
- Secondary server ns2.example.com also rejected AXFR request
- No sensitive data was leaked
- Demonstrated proper DNS hardening on the test domain

## Lessons Learned
- Zone transfers are a legacy DNS feature that can become a security risk if not disabled or restricted
- Attackers can use successful zone transfers to map out network infrastructure
- Best practices include:
  - Restricting AXFR requests to trusted IPs
  - Disabling zone transfers if not required
  - Monitoring DNS logs for unauthorized AXFR attempts
