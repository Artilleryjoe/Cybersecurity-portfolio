# Lab 24: Encrypting and Decrypting with AES

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to use the Advanced Encryption Standard (AES) algorithm to encrypt and decrypt a file. AES is a symmetric encryption standard widely used for securing data at rest and in transit.

## Tools Used  
- OpenSSL (Linux)  
- Sample plaintext file  
- Terminal / Command Prompt  
- AES-256-CBC encryption mode

## Procedure  
- Create a test file with sensitive data:
  ```bash
  echo "This is a secret message." > secret.txt
- Encrypt the file using AES-256-CBC:
  ```bash
  openssl enc -aes-256-cbc -salt -in secret.txt -out secret.enc
  - You will be prompted to enter and verify a password (used as the encryption key)
- Decrypt the file using the same password:
  ```bash
  openssl enc -aes-256-cbc -d -in secret.enc -out decrypted.txt
- View the decrypted output:
  ```bash
  cat decrypted.txt
  
## Results
- Original file (secret.txt) was encrypted into a binary .enc file
- Decrypted file matched the original plaintext exactly
- AES-256-CBC encryption required a password for both encryption and decryption
- Confirmed symmetric key behavior: same key used for both operations

## Lessons Learned
- AES is fast, secure, and widely used in modern cryptographic systems
- Symmetric encryption requires careful key management — anyone with the key can decrypt the data
- OpenSSL provides an accessible way to practice encryption in real-world formats
- Salting adds randomness to prevent identical plaintexts from producing identical ciphertexts
