# Starting a Live Packet Capture Using Kali Linux Terminal

## Course  
CYB/530 – Cybersecurity Practitioner

## Objective  
This lab demonstrates how to initiate a live network packet capture in Kali Linux using terminal-based tools. Capturing live packets is foundational for real-time threat detection, forensic analysis, and traffic visibility in enterprise environments.

## Tools Used  
- Kali Linux (Rolling)  
- `tcpdump` (terminal-based packet capture tool)  
- Optional: `wireshark` for GUI-based analysis post-capture

## Procedure  

- Open a terminal in Kali Linux
- Identify available network interfaces:
  ```bash
  ip link show
- Begin live capture on selected interface (e.g., eth0 or wlan0):
    ```bash
    sudo tcpdump -i eth0
- To save captured packets to a ```.pcap``` file for later analysis:
    ```bash
    sudo tcpdump -i eth0 -w capture_output.pcap
- Let the capture run for a short period while browsing or generating traffic
- Stop capture using ```Ctrl + C```
- Review basic output in terminal or load ```.pcap``` into Wireshark:
    ```bash
    wireshark capture_output.pcap
## Results
- Successfully captured live packet data from the selected network interface
- Captured packets included ARP requests, DNS lookups, and HTTP traffic
- ```.pcap``` file was saved and verified in Wireshark for deeper inspection
Traffic timestamps, source/destination IPs, and protocol types were visible

## Lessons Learned
- ```tcpdump``` provides powerful, scriptable packet capture from the command line
- Live packet capture is essential for detecting anomalies and understanding network behavior
- Saving to ```.pcap``` allows collaboration and further analysis with tools like Wireshark
- Elevated privileges (sudo) are required to access raw packet data
