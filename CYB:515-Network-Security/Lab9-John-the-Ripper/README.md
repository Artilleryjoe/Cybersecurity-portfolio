# Using John the Ripper to Crack Password Hashes

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use John the Ripper, a popular open-source password cracking tool, to analyze and crack password hashes. The exercise highlights the importance of using strong hashing algorithms and secure password practices.

**Disclaimer:** This lab was conducted using password hashes generated from test user accounts in a controlled environment. No unauthorized systems or data were accessed.

## Tools Used  
- John the Ripper (Community Edition)  
- Kali Linux or Ubuntu  
- Sample password hash file (Linux `/etc/shadow`, or manually generated hash)

## Procedure  

- Install John the Ripper (if not already present):
    ```bash
    sudo apt update
    sudo apt install john
- Create a test password hash using OpenSSL or generate test users:
    ```bash
    openssl passwd -1 "MyTestPassword"
- Save the hash into a file called test_hash.txt:
    ```bash
    user:$1$abcdefgh$1234567890abcdefghi.:0:0:99999:7:::
- Run John to begin cracking the hash:
    ```bash
    john test_hash.txt
- Optionally, use a custom wordlist:
    ```bash
    john --wordlist=/usr/share/wordlists/rockyou.txt test_hash.txt

## Results
- John successfully identified weak or common passwords in test hashes
- With the default or custom wordlist, hashes using simple passwords were cracked in seconds
- Hashes based on long or complex passwords resisted cracking attempts within the test duration
- Demonstrated the effectiveness of salted hashing and password length as defensive controls

## Lessons Learned
- Weak, unsalted, or short passwords are highly vulnerable to dictionary attacks
- John the Ripper simulates real-world brute force and dictionary-based cracking scenarios
- Hash cracking is essential for red teams and vital for blue teams to understand password policy risk
- Passwords should be long, complex, and stored with strong, salted hashing algorithms (e.g., bcrypt, scrypt, Argon2)bash
