# Bypassing Command Shell Restrictions

## Course  
CYB/550 – Technical Enterprise Security

## Objective  
This lab demonstrates how to bypass restricted shell environments using techniques that allow the user to escape confinement and gain access to a fully functional command shell. This simulates how attackers escalate privileges or evade sandboxing mechanisms.

## Tools Used  
- Restricted Linux shell (e.g., rbash)  
- Bash, Python  
- Terminal access to confined environment

## Procedure  
- Log into a restricted shell environment (`rbash` or custom jailed shell)  
- Attempt to run standard commands (e.g., `cd`, `ls`) to verify restrictions  
- Use environment variable manipulation to bypass path restrictions:
  ```bash
  export PATH=/bin:/usr/bin
- Spawn an unrestricted shell using:
  ```bash
  python -c 'import pty; pty.spawn("/bin/bash")'
- If Python is not available, attempt:
    ```bash
    /bin/sh
    bash -i
- Redirect or manipulate known programs to escalate shell access using symlinks or wildcard injection, if permitted

## Results
- Initial shell restricted execution of built-in commands
- Successfully escaped the restricted environment using Python to spawn a new shell
- Gained access to full Bash prompt and executed previously blocked commands
- Verified access by creating files and navigating directories

## Lessons Learned
- Restricted shells provide weak security if fallback binaries or interpreters are available
- Attackers frequently chain together local exploits with shell escapes for lateral movement
- Proper sandboxing requires tools like chroot jails, AppArmor, or Docker with enforced seccomp profiles
- Auditing shell access and enforcing least privilege are critical to limiting exposure
