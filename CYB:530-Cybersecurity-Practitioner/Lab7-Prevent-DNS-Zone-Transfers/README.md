# Preventing DNS Zone Transfers

## Course  
CYB/530 – Cybersecurity Practitioner

## Objective  
This lab demonstrates how to prevent unauthorized DNS zone transfers, a common misconfiguration that can expose internal network structure. Restricting zone transfers enhances DNS security and mitigates reconnaissance by external attackers.

## Tools Used  
- Windows Server DNS or BIND on Linux  
- nslookup or dig for testing  
- Administrative tools or terminal editor  

## Procedure  
- Attempt a DNS zone transfer from a non-authorized client:
  - Using `dig`:
    ```bash
    dig @dns-server-ip example.com AXFR
    ```
  - Using `nslookup`:
    ```plaintext
    nslookup
    > server dns-server-ip
    > set type=AXFR
    > example.com
    ```

- On Windows Server:
  - Open DNS Manager  
  - Right-click the target zone and open **Properties**  
  - Navigate to the **Zone Transfers** tab  
  - Disable zone transfers entirely, or restrict them to listed name servers

- On BIND:
  - Open the DNS zone configuration file (e.g., `/etc/bind/named.conf.local`)  
  - Add or update the zone block to:
    ```bash
    zone "example.com" {
        type master;
        file "/etc/bind/db.example.com";
        allow-transfer { none; };
    };
    ```
  - Restart the BIND service:
    ```bash
    sudo systemctl restart bind9
    ```

- Reattempt the zone transfer to confirm access is denied

## Results  
- Initial test allowed complete DNS zone enumeration  
- After reconfiguration, zone transfer attempts were refused or failed  
- DNS service continued to operate normally for standard queries  
- Confirmed hardened configuration using both `dig` and `nslookup`

## Lessons Learned  
- Zone transfers should never be exposed to unauthorized clients  
- Misconfigured DNS services can leak valuable reconnaissance data  
- Hardening DNS is essential to protecting internal infrastructure  
- Regular testing and auditing of DNS permissions improves long-term security posture
