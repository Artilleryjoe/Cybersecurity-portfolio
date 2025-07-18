# Scanning the Local Network

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to scan the local network by probing the target system’s ports to identify which are open and gather information about services.

## Tools Used  
- nmap (Network Mapper)

## Procedure  
- Ping the target IP to verify connectivity:
  ```bash
  ping 192.168.56.101
  ```
- Stop the ping command (Ctrl+C).  
- Run an `nmap` scan with verbosity, OS detection, version detection, and script scanning:
  ```bash
  nmap -v -A -sV 192.168.56.101
  ```

## Results  
- Successfully mapped the target network.  
- Discovered open ports and gathered service/version information for reconnaissance.

## Lessons Learned  
- `nmap` is a powerful tool for network discovery and security auditing.  
- Scanning with flags like `-A` and `-sV` provides detailed info about hosts.  
- Understanding network topology is critical for effective penetration testing and defense.


