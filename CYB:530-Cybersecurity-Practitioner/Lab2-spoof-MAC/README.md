# Spoofing a MAC Address Using SMAC

## Course  
CYB/530 – Cybersecurity Practitioner

## Objective  
This lab demonstrates how to spoof a MAC (Media Access Control) address using SMAC, a Windows-based GUI tool. MAC spoofing is a technique used to mask or change the hardware address of a network interface, commonly used for anonymity, evasion, or testing network-based access controls.

**Disclaimer:** This lab was performed in an isolated, legal test environment. Unauthorized MAC spoofing on production networks or third-party systems is prohibited and unethical.

## Tools Used  
- Windows 10 VM  
- SMAC MAC Address Changer (Trial or Licensed)  
- Command Prompt (`ipconfig`, `getmac`) for verification  
- Wireshark (optional, for verifying on-wire changes)

## Procedure  

- Install and launch SMAC on a Windows machine with admin privileges
- Identify the active network adapter from the list displayed
- Note the current (real) MAC address using:
    ```cmd
    getmac /v
- In SMAC, select the target adapter and enter a new spoofed MAC address:
    - Format: 12 hexadecimal digits (e.g., 00:11:22:33:44:55)
    - Avoid multicast or locally administered address conflicts
- Apply the change and reboot if prompted

- Verify that the spoofed MAC address has been applied:
    ```bash
    ipconfig /all
    getmac /v

## Results
- SMAC successfully applied the spoofed MAC address to the network adapter
- Command-line tools confirmed the new MAC was active and recognized by the OS
- Outbound traffic reflected the spoofed MAC on the local network
- No connectivity loss occurred during testing

## Lessons Learned
- MAC address spoofing is simple but powerful for both legitimate testing and adversarial evasion
- Some networks rely on MAC filtering for access control, making spoofing a relevant security concern
- Detection of spoofed MAC addresses requires network monitoring and anomaly detection tools
- MAC address changes do not persist through all reboots or hardware resets without proper configuration



