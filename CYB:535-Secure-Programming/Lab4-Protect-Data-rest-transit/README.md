# Protecting Data in Transit and Data at Rest

## Course  
CYB/535 – Secure Programming

## Objective  
This lab demonstrates methods to secure sensitive data both during transmission and when stored. Proper handling of data in transit and at rest is essential to prevent eavesdropping, tampering, or unauthorized access.

## Tools Used  
- Python 3.x  
- Flask  
- OpenSSL (for HTTPS certificate generation)  
- PyCryptodome (for encryption at rest)  
- PyCharm  

## Procedure  

### Protecting Data in Transit
- Generate a self-signed certificate using OpenSSL:
  ```bash
  openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
- Update the Flask application to serve over HTTPS:
    ```python
    if __name__ == '__main__':
    app.run(ssl_context=('cert.pem', 'key.pem'))
- Verify browser communication used HTTPS and no plaintext credentials appeared in transit
- Confirm certificate-based encryption using developer tools (lock icon, TLS connection)
  ***Protecting Data at Rest***
  - Installed PyCryptodome:
      ```bash
      pip install pycrytodome
  - Added AES encryption for sensitive data storage:
        ```python
        from Crypto.Cipher import AES
        from Crypto.Random import get_random_bytes
        import base64
        
        def encrypt_data(plaintext, key):
            cipher = AES.new(key, AES.MODE_EAX)
            nonce = cipher.nonce
            ciphertext, tag = cipher.encrypt_and_digest(plaintext.encode())
            return base64.b64encode(nonce + ciphertext).decode()
        
        def decrypt_data(encoded, key):
            raw = base64.b64decode(encoded)
            nonce = raw[:16]
            ciphertext = raw[16:]
            cipher = AES.new(key, AES.MODE_EAX, nonce=nonce)
            return cipher.decrypt(ciphertext).decode()
  
  ## Results
- Web traffic between client and server was successfully encrypted using HTTPS
- Packet sniffing attempts confirmed that no sensitive information was transmitted in plaintext
- Sensitive user data was encrypted before writing to disk
- Encrypted data could only be decrypted with the correct key, preventing unauthorized reads

## Lessons Learned
- HTTPS is essential for securing web communication — even during development
- Encryption at rest must be applied before persistence, not just during transport
- Proper key management is vital — hardcoding or leaking keys undermines encryption
- Combining encryption in transit and at rest provides layered data protection

