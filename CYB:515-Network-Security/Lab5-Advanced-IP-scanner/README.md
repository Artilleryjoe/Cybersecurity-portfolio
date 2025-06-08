# Using Advanced IP Scanner for Network Discovery

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use Advanced IP Scanner to identify live hosts, open ports, shared folders, and device information on a local area network. The tool is useful for quickly mapping small enterprise or home office networks.

## Tools Used  
- Advanced IP Scanner (Windows)  
- Windows 10 virtual machine  
- Local network or test subnet  
- Optional: Open services or shared folders on other VMs for scanning

## Procedure  

- Download and install Advanced IP Scanner from the official website

- Launch the application and enter the target subnet (e.g., `192.168.1.0/24`)

- Begin the scan:
  - Click **Scan** and wait for it to complete

- Review results:
  - Identify online devices by IP and hostname  
  - Note any open ports (e.g., RDP, HTTP)  
  - Detect shared folders and remote access services (if available)

- Test functionality:
  - Attempt to open a shared folder from the interface  
  - Use remote desktop or SSH tools if services are detected and allowed

## Results  
- Advanced IP Scanner successfully identified all active hosts in the subnet  
- Detected shared folders and open ports on configured VMs  
- Exported results to CSV for documentation  
- Observed fast scan performance and responsive UI

## Lessons Learned  
- Advanced IP Scanner is a user-friendly reconnaissance tool for network mapping  
- While limited compared to tools like Nmap, it offers quick insight into asset visibility  
- Regular scanning helps identify unauthorized devices or exposed services  
- Enumeration tools should always be used with authorization and documented scope in enterprise environments
