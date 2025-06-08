# Observing a SHA-Generated Hash Value

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to generate and observe SHA (Secure Hash Algorithm) hash values using commonly available tools. The goal is to understand how file contents are transformed into fixed-length, unique hash values that support data integrity and authentication in enterprise systems.

## Tools Used  
- Linux terminal  
- `sha1sum`, `sha256sum`, or `sha512sum`  
- Sample plaintext file

## Procedure  

- Create a sample file:
    ```bash
    echo "This is a test for SHA hashing." > sample.txt
- Generate a SHA-1 hash:
    ```bash
    sha1sum sample.txt
-Generate a SHA-256 hash:
    ```bash
    sha256sum sample.txt
-Generate a SHA-512 hash:
    ```bash
    sha512sum sample.txt
- Modify the file slightly and regenerate the hash:
    ```bash
    echo "!" >> sample.txt
    sha256sum sample.txt
- Observe the differences between the original and modified hash values

## Results
- SHA-1, SHA-256, and SHA-512 hashes were successfully generated
- Each hash algorithm produced a fixed-length output unique to the file contents
- Even a 1-character change produced a completely different hash (avalanche effect)
- Demonstrated how hashes ensure integrity without revealing file contents

## Lessons Learned
- SHA algorithms are fundamental to modern cybersecurity systems
- Hashes are deterministic but non-reversible — they verify but do not encrypt
- Longer hash lengths (e.g., SHA-256, SHA-512) provide greater resistance to collisions
- Integrity verification using SHA is critical for secure file distribution and digital forensics

