# Lab 23: Encrypting and Decrypting Using Kleopatra

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to use Kleopatra, a GUI frontend for Gpg4win, to encrypt and decrypt files using public key cryptography. The exercise reinforces the principles of confidentiality and asymmetric encryption in practical data protection.

## Tools Used  
- Kleopatra (part of Gpg4win suite)  
- Windows OS  
- Generated key pair  
- Sample text file for encryption

## Procedure  
- Install Gpg4win and launch Kleopatra  
- Generate a key pair:
  - Click **"File" > "New Certificate"**
  - Select **"Create a personal OpenPGP key pair"**
  - Enter name and email, then proceed through prompts
  - Save the key pair and back up the revocation certificate
- Create a plain text file (e.g., `message.txt`) containing test content
- Right-click the file and choose **"Sign and/or Encrypt"**  
  - Select **"Encrypt"**, then choose your recipient key  
  - The output will be a `.gpg` encrypted file
- To decrypt:
  - Right-click the `.gpg` file and choose **"Decrypt and Verify"**
  - Enter passphrase if prompted  
  - Kleopatra will output the original plaintext file

## Results  
- Successfully generated OpenPGP key pair with Kleopatra  
- Encrypted a test file using public key encryption  
- Decrypted the file using the associated private key  
- Verified the confidentiality and integrity of the original message

## Lessons Learned  
- Public key cryptography separates encryption and decryption responsibilities, enhancing security  
- Kleopatra provides a user-friendly way to manage OpenPGP keys and encrypt files  
- Key management (including backup and revocation) is critical in secure communication  
- Even simple GUI tools enforce fundamental concepts in cryptographic workflows

