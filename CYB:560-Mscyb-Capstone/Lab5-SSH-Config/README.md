# Configuring an SSH Server

## Course  
CYB/560 – MS Cybersecurity Capstone

## Objective  
This lab demonstrates how to securely configure an OpenSSH server to allow encrypted remote shell access, including user authentication, service hardening, and basic auditing. This setup is a foundational component of secure system administration and remote access control.

## Tools Used  
- Linux system (Ubuntu/Debian/CentOS)  
- `openssh-server` package  
- Terminal with sudo/root access  
- Text editor (`nano`, `vim`, or similar)

## Procedure  
- Update system packages:
  ```bash
  sudo apt update && sudo apt upgrade
- Install OpenSSH server:
    ```bash
    sudo apt install openssh-server
- Verify the SSH service is running:
    ```bash
    sudo systemctl status ssh
- Edit the SSH config file:
    ```bash
    sudo nano /etc/ssh/sshd_config
- Make the following hardening changes:

- Disable root login: PermitRootLogin no

- Change port: Port 2222 (or another non-default port)

- Limit users: AllowUsers yourusername

- Enforce protocol version 2: Protocol 2

- Restart SSH service:
    ```bash
    sudo systemctl restart ssh
- Open a remote terminal and connect:
    ```bash
    ssh yourusername@your.server.ip -p 2222
- Monitor /var/log/auth.log for login attempts

## Results
- SSH server installed and operational on custom port
- Root login blocked; user-based authentication configured
- Verified remote connection and login logging
- Observed successful connection using public key authentication (if implemented)

## Lessons Learned
- Secure SSH configuration is critical for reducing attack surface
- Changing defaults and restricting access improves defense-in-depth
- SSH provides encrypted, authenticated, and auditable access
- Misconfiguration can lead to open attack vectors or service denial
