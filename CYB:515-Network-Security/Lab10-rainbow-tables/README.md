# Using Rainbow Tables to Crack Password Hashes

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use rainbow tables to recover passwords from unsalted hash values. The goal is to understand the concept of precomputed attacks and why modern password storage methods must include salting and computational hardening.

**Disclaimer:** All hashes were generated from test passwords in a closed lab environment. No real credentials or external systems were used.

## Tools Used  
- `rtgen` and `rcracki_mt` (RainbowCrack toolkit)  
- Precomputed rainbow tables (LM/NTLM)  
- Kali Linux or Windows test environment  
- Sample hashes (e.g., NTLM hashes from a test account)

## Procedure  

- Download or generate rainbow tables:
  - Common types: LM, NTLM, MD5 (unsalted only)
  - Precomputed tables can be downloaded or built using:
    ```bash
    rtgen ntlm loweralpha-numeric 1 8 0 2400 80000000
    ```

- Sort and finalize the tables:
  ```bash
  rtsort .
- Save a test hash in a file (hashes.txt), such as:
    ```bash
    32ed87bdb5fdc5e9cba88547376818d4
- Run rcracki_mt against the hash:
    ```bash
    rcracki_mt . -h 32ed87bdb5fdc5e9cba88547376818d4
- Observe if the hash is found in the precomputed table

## Results
- Rainbow table successfully cracked simple, unsalted hashes (e.g., "password123")
- Lookup was nearly instantaneous due to precomputation
- Complex or salted hashes could not be cracked with this method
- Demonstrated efficiency and limitations of this type of attack

## Lessons Learned
- Rainbow tables are powerful against unsalted hashes but ineffective against modern, salted schemes
- Passwords must be hashed using functions that include:
    - Salts (unique per user)
    - Slow hashing (e.g., bcrypt, scrypt, Argon2)
- Defenders must store credentials securely and detect tools like RainbowCrack through system monitoring
- Attackers can leverage rainbow tables for instant credential recovery on legacy systems



