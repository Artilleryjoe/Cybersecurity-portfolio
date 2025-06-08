# Cracking a Windows Password Using Ophcrack

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use Ophcrack, a password-cracking tool, to recover Windows user account passwords from NTLM hashes using rainbow tables. The purpose is to understand how weak or short passwords can be recovered without brute-force attacks, emphasizing the need for secure password practices.

**Disclaimer:** This lab was performed in a controlled virtual environment using a test Windows VM. No unauthorized access attempts were made, and only approved accounts were targeted.

## Tools Used  
- Ophcrack LiveCD or pre-installed application  
- Windows 10/11 virtual machine with known test user account  
- VirtualBox or Hyper-V (for VM hosting)

## Procedure  

- Create a test user on the Windows VM with a weak password (e.g., `password123`)

- Download the Ophcrack LiveCD ISO from the official site and boot it in a VM

- Attach the Windows virtual disk as a secondary disk in the Ophcrack environment

- Let Ophcrack automatically scan for Windows installations and retrieve user hashes

- Select a user and begin hash cracking using the built-in rainbow tables

- Observe whether the plaintext password is recovered

- (Optional) Download and add additional rainbow tables for longer passwords

## Results  
- Ophcrack successfully detected the Windows SAM file and extracted NTLM hashes  
- Weak test passwords (e.g., `123456`, `password123`) were cracked in seconds  
- Stronger passwords or longer passphrases were not recovered without additional rainbow tables  
- Demonstrated how precomputed hashes (rainbow tables) are a serious threat to reused or simple passwords

## Lessons Learned  
- Passwords stored as unsalted hashes are vulnerable to rainbow table attacks  
- Short, weak, or commonly used passwords can be easily recovered  
- Password policies must enforce complexity and length to resist offline attacks  
- Tools like Ophcrack highlight the importance of using password hashing best practices (e.g., salting, slow hashes)
