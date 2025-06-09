# Using RSA Asymmetric Algorithm

## Course  
CYB/540 – Cryptography

## Objective  
This lab demonstrates how to use RSA to encrypt and decrypt messages with asymmetric keys. Asymmetric cryptography enables secure message exchange, digital signatures, and identity validation without sharing a secret key.

## Tools Used  
- OpenSSL  
- Linux terminal or Windows with OpenSSL installed  
- `private_key.pem` and `public_key.pem` from prior lab  
- Plaintext message file (`message.txt`)  

## Procedure  

- Create a plaintext message:
    ```bash
    echo "Confidential: Project launch delayed 30 days." > message.txt
- Encrypt the message using the public key:
    ```bash
    openssl rsautl -encrypt -inkey public_key.pem -pubin -in message.txt -out message.enc
- Verify the encrypted file is unreadable in plain text:
    ```bash
    cat message.enc
- Decrypt the message using the private key:
    ```bash
    openssl rsautl -decrypt -inkey private_key.pem -in message.enc -out message_decrypted.txt
- Confirm the decrypted message matches the original:
    ```bash
    cat message_decrypted.txt

## Results
- The original plaintext is encrypted into a binary .enc file using the public key
- Decryption with the private key successfully restores the original content
- The process confirms the unidirectional nature of RSA key use — only the private key can decrypt data encrypted with its matching public key

## Lessons Learned
- RSA allows secure communication without prior key exchange
- Public keys can encrypt, but only private keys can decrypt
- The integrity and confidentiality of communications depend on secure key storage
- Asymmetric encryption is slower than symmetric but vital for identity and trust in distributed systems
