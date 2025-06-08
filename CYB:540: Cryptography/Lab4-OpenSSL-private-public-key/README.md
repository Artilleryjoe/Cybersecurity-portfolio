# OpenSSL Private/Public Key Pair Generation

## Course  
CYB/540 – Cryptography

## Objective  
This lab demonstrates how to generate an RSA public/private key pair using OpenSSL. Key pairs are foundational to asymmetric encryption, digital signatures, and secure certificate-based authentication.

## Tools Used  
- OpenSSL  
- Linux terminal or Windows with OpenSSL installed  
- Text editor (for inspection and optional backup of keys)

## Procedure  

- Open a terminal session  
- Generate a new 2048-bit RSA private key:
  ```bash
  openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048
- Verify the private key file is created and readable:
  ```bash
  cat private_key.pem
- Extract the corresponding public key:
    ```bash
    openssl rsa -pubout -in private_key.pem -out public_key.pem
- View the public key:
-Optionally, protect the private key with a passphrase:
    ```bash
    openssl genpkey -aes256 -algorithm RSA -out private_key_secure.pem

## Results
The private key is generated and saved as private_key.pem
The corresponding public key is extracted as public_key.pem
Keys are valid and readable in PEM format
A secure version of the private key can be protected with encryption

## Lessons Learned
RSA key pairs are essential to secure communications and identity verification
The private key must be stored securely and never shared
The public key can be freely distributed and used to verify or encrypt data
OpenSSL provides a powerful, scriptable way to generate and manage cryptographic keys
