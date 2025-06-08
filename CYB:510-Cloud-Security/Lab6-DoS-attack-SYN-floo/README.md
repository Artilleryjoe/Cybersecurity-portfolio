# Performing a DoS Attack Using a SYN Flood

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates a Denial-of-Service (DoS) attack using a SYN flood technique. The attacker overwhelms a target system with a high volume of TCP SYN requests, exhausting system resources by exploiting the TCP three-way handshake mechanism.

**Note:** This lab is performed in a closed, controlled environment and not against any public or unauthorized system.

## Tools Used  
- Kali Linux or equivalent attacker system  
- hping3 or nping (from Nmap suite)  
- Target Linux VM with open TCP port (e.g., Apache or Netcat listener)  
- Wireshark (optional, for packet analysis)

## Procedure  

- Install necessary tools (if not already present):
  ```bash
  sudo apt update
  sudo apt install hping3 nmap
- On the target machine, open a port for monitoring (e.g., using netcat):
  ```bash
  nc -lvp 80
- On the attacker machine, launch a SYN flood using ```hping3```:
  ```bash
- Or using ```nping```:
    ```bash
    sudo nping --tcp -p 80 --flags syn --rate 1000 <target-IP>
- Monitor the target system:
    - Use netstat -an | grep SYN_RECV to view half-open connections
    - Use top or htop to monitor CPU/memory impact
    - Optionally capture traffic in Wireshark for visual analysis
- Stop the attack after observation and reset services as needed
## Results
- The SYN flood generated hundreds/thousands of half-open connections
- Target system showed multiple connections in SYN_RECV state
- In some cases, service performance degraded or temporarily froze
- Attack successfully demonstrated how easily TCP resources can be exhausted

## Lessons Learned
- SYN floods exploit the TCP handshake by never completing the connection
- Modern systems may implement SYN cookies or rate-limiting to defend against this type of attack
- Even basic tools like hping3 and nping can simulate powerful DoS conditions
- Performing these tests in a lab helps reinforce the importance of IDS/IPS and firewall tuning
