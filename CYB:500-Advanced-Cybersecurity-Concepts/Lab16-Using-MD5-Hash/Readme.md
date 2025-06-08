# Lab 16: Using the MD5 Hash Algorithm

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
Demonstrate how to calculate and verify the MD5 hash of a file using a Windows-based MD5 utility. This process illustrates how hashing algorithms are used to verify file integrity and detect tampering.

## Tools Used  
- Windows OS  
- winMD5 tool (or equivalent)  
- Sample file for hashing  

## Procedure  
- Create a simple practice file (e.g., `echo Hello > testfile.txt`)
- Open winMD5 (or equivalent hashing utility)
- Load the `testfile.txt` file into the utility
- Observe and copy the generated MD5 checksum
- Rename the file to `md5hash.txt` (or appropriate label for reference)
- Paste the copied checksum into a secure location or verification document
- Reopen or rehash the file later to verify the hash remains unchanged

## Results  
- The MD5 hash for the original file was successfully generated  
- Renaming the file did not affect its hash, confirming file content is the same  
- Any change in file content resulted in a different MD5 hash

## Lessons Learned  
- MD5 can be used to verify file integrity but is **not** secure for cryptographic purposes due to collision vulnerabilities  
- File hashes are helpful for checking tampering during downloads or transfers  
- Even a single-byte change will drastically alter the MD5 hash output  
- For stronger security needs, use SHA-256 or SHA-3 instead of MD5


