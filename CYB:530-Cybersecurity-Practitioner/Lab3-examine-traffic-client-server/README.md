# Examining Traffic Between Client and Server

## Course  
CYB/530 – Cybersecurity Practitioner

## Objective  
This lab demonstrates how to examine and analyze traffic between a client and server using packet capture tools. The goal is to identify key protocol exchanges, validate expected communication patterns, and observe potential security implications in plaintext or poorly secured connections.

## Tools Used  
- Kali Linux or Windows with Wireshark  
- Web browser (acting as client)  
- Local or cloud-based HTTP/HTTPS server  
- tcpdump (optional, for terminal-based capture)

## Procedure  

- Launch Wireshark and begin capturing traffic on the active network interface
- On the client system, initiate communication with the server (e.g., browsing a webpage or submitting a form):
  - Example: Visit `http://testserver.local` or `http://192.168.1.100`
- Stop the capture after several seconds of communication
- Filter traffic in Wireshark using:
  ```wireshark
  ip.addr == [client_IP] && ip.addr == [server_IP]
- Analyze the following elements:
- TCP handshake (SYN → SYN/ACK → ACK)
- HTTP GET/POST requests
- Server HTTP responses (e.g., 200 OK, 404 Not Found)
- Presence or absence of TLS encryption
- Note any sensitive data visible in plaintext (for HTTP)
- For HTTPS traffic, note the encrypted payload and TLS handshake details

## Results
- Successful packet capture showed full TCP handshakes between the client and server
- HTTP traffic was visible in plaintext, including full URLs and header information
- HTTPS traffic showed TLS negotiation but encrypted content, validating encryption in transit
- Identified session cookies and user-agent strings that could be valuable in session hijacking if unprotected

## Lessons Learned
- Packet captures are vital for understanding the security posture of client-server communication
- Unencrypted protocols expose sensitive data and should be avoided in production environments
- Even encrypted sessions can leak metadata (like DNS or certificate info) without proper hardening
- Monitoring client-server traffic helps detect anomalies, intrusion attempts, and insecure configurations
